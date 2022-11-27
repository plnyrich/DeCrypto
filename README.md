# Cryptominers Detector
DeCrypto (cryptominers detection software) is implemented as a NEMEA module. The detector takes as input flows from the exporter and sends them to its output flows marked as a miner.

Before the first run, Cython modules need to be compiled:
./configure.sh

The detector has several customizable options, available via -h argument.
```
usage: minerdetector.py [-h] [-m MODEL] [-b BUFFER] [-c] [-f] [-i I] [-d DST_THRESHOLD] [-t ML_THRESHOLD] [-v]

optional arguments:
  -h, --help            show this help message and exit
  -m MODEL, --model MODEL
                        Pickle file with ML model, default is ../models/data_symmetry.pickle
  -b BUFFER, --buffer BUFFER
                        Flow buffer size, default is 100000
  -c, --use-dst-cache   Cache DST output and use as prefilter in ML
  -f, --filter          Filter flows with DST PORT/443 without SNI
  -i I                  IFC interfaces for pytrap
  -d DST_THRESHOLD, --dst-threshold DST_THRESHOLD
                        Threshold for miners' DST pignistic function [0..1], default is 0.03
  -t ML_THRESHOLD, --ml-threshold ML_THRESHOLD
                        Threshold for ML proba [0..1], default is 0.99
  -v, --verify-mode     Run detector in verification mode, flow labels are required
```

## Requirements
* [cython](https://cython.org/)
* [pandas](https://pandas.pydata.org/)
* [pytrap](https://github.com/CESNET/Nemea-Framework/tree/34219c9a0db3dbab1d8e4de072a2d641f160002b/pytrap)
* [re2](https://github.com/google/re2)

## Additional Resources
Datasets with cryptominer communication can be found [here](https://zenodo.org/record/7189293).

Traffic capture rules generator can be found [here](https://github.com/plnyrich/RulesGenerator).


## Acknowledgements
This research was funded by the Ministry of Interior of the Czech Republic, grant No. VJ02010024: Flow-Based Encrypted Traffic Analysis and also by the Grant Agency of the CTU in Prague, grant No. SGS20/210/OHK3/3T/18 funded by the MEYS of the Czech Republic.