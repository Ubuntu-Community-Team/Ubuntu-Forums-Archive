---
title: "problem installing new programs"
date: 2007-05-15
forum: Desktop Environments
---

### Post by rkakkar on 2007-05-15
every time i start adept manager, it throws me the following error

> You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.

however i have no such process running.. this is the output of "top"

```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4909 root      15   0  219m  22m 4564 R 10.6  4.5   0:37.46 Xorg
 5467 rahul     15   0  145m  42m  22m S  2.7  8.6   0:22.20 swiftfox-bin
 5060 rahul     15   0 34332  16m  12m S  1.3  3.3   0:06.10 kicker
 5056 rahul     15   0 30328  11m 9576 S  0.7  2.4   0:02.10 kwin
 5504 rahul     15   0 34116  15m  12m R  0.7  3.2   0:01.38 konsole
 5043 rahul     18   0 25632 3080 1760 S  0.3  0.6   0:00.34 dcopserver
 5521 rahul     15   0  2320 1160  880 R  0.3  0.2   0:00.07 top
    1 root      18   0  2912 1844  524 S  0.0  0.4   0:01.56 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    7 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
  107 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
  128 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  129 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  130 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  131 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1942 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd
 1943 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1960 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 ata/0
 1961 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux
 2066 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0
 2067 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 scsi_eh_1
 2263 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kjournald
 2462 root      21  -4  2892 1236  372 S  0.0  0.2   0:00.55 udevd
 3331 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd
 3377 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused
 4049 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty
 4050 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty
 4052 root      18   0  1652  512  440 S  0.0  0.1   0:00.00 getty
 4053 root      18   0  1652  508  440 S  0.0  0.1   0:00.00 getty             
```

---

### Post by Nythain on 2007-05-15
sudo dpkg --configure -a
sudo aptitude clean
sudo aptitude update

---

### Post by rkakkar on 2007-05-15
that did the trick!! thanks man :).. could you tell me what exactly happened that we needed to "clean"? what does the --configure -a option do?

---

