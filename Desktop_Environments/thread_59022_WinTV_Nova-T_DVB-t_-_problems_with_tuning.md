---
title: "WinTV Nova-T DVB-t - problems with tuning"
date: 2005-08-22
forum: Desktop Environments
---

### Post by tag on 2005-08-22
I have a Hauppauge WinTV Nova DVB-T PCI-card that is not working properly. Apparently it is fully registered in the system with all kernel modules loaded. I have the regional transmission frequencies listed correnctly in the config file, but still neither scan nor kaffeine are able to tune into a tv station. This is what I get from a scan:

```
tag@fry:~/.tzap$ scan /home/tag/.kde/share/apps/kaffeine/dvb-t/de-Koeln-Bonn
scanning /home/tag/.kde/share/apps/kaffeine/dvb-t/de-Koeln-Bonn
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 538000000 0 2 0 1 1 3 0
initial transponder 514000000 0 2 0 1 1 3 0
initial transponder 698000000 0 2 0 1 1 3 0
initial transponder 650000000 0 2 0 1 1 3 0
initial transponder 826000000 0 2 0 1 1 3 0
initial transponder 834000000 0 2 0 1 1 3 0
>>> tune to: 538000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 538000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 514000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 514000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 698000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 698000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 650000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 650000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 826000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 826000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 834000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 834000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSI
ON_MODE_8K:GUARD_INTERVAL_1_4:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.
```

Has anybody got an idea on how to fix this?
Btw.: I use an indoor antenna which used to work fine under windows and the proprietary Hauppauge software.

---

