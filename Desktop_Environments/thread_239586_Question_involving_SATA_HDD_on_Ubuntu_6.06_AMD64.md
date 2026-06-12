---
title: "Question involving SATA HDD on Ubuntu 6.06 AMD64"
date: 2006-08-19
forum: Desktop Environments
---

### Post by Theimon on 2006-08-19
I've got Ubuntu installed on a Maxtor DiamondMax 10 SATA I disk, which works fine. I did notice that copying files sometimes took a while (longer than normal), as well as on the SATA disk it self as from or to the SATA disk. My system contains 2 other HDDs which are both ATA/IDE. 

After doing some searching I found the hdparm command, which gives me the following output for the 3 devices:
```

theimon@CP353526-a:~$ sudo hdparm /dev/hda

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 156355584, start = 0
theimon@CP353526-a:~$ sudo hdparm /dev/hdb

/dev/hdb:
 multcount    =  0 (off)
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 234375000, start = 0
theimon@CP353526-a:~$ sudo hdparm /dev/sda

/dev/sda:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 30401/255/63, sectors = 488397168, start = 0
theimon@CP353526-a:~$

```
No DMA mentioned for /dev/sda and 16-bit support where 32bit should be normal (it's a fairly modern drive). So did some more searching and found out that sdparm is used for SATA/SCSI disks. I installed it using Synaptic and ran it in console, which then gave me this output:
```

    /dev/sda: ATA       Maxtor 6L250S0    BACE
Read write error recovery mode page:
  AWRE        1
  ARRE        1
  TB          0
  RC          0
  EER         0
  PER         0
  DTE         0
  DCR         0
  RRC         0
  COR_S       0
  HOC         0
  DSOC        0
  WRC         0
  RTL         0
Caching (SBC) mode page:
  IC          0
  ABPF        0
  CAP         0
  DISC        0
  SIZE        0
  WCE         1
  MF          0
  RCD         0
  DRRP        0
  WRP         0
  DPTL        0
  MIPF        0
  MAPF        0
  MAPFC       0
  FSW         0
  LBCSS       0
  DRA         0
  NV_DIS      0
  NCS         0
  CSS         0
Control mode page:
  TST         0
  TMF_ONLY    0
  D_SENSE     0
  GLTSD       1
  RLEC        0
  QAM         0
  QERR        0
  RAC         0
  UA_INTLCK   0
  SWP         0
  ATO         0
  TAS         0
  AUTOLOAD    0
  BTP        -1
  ESTCT      30
theimon@CP353526-a:~$

```
And even when looking through the man.pages, i can't really make anything of it all. What does surprise me tho is this entry right after giving the command:
```

    /dev/sda: ATA       Maxtor 6L250S0    BACE

```
Ubuntu doesn't recognize it's a SATA device? So maybe that's why I can't seem to find a way to enable DMA or the 32-bits IO support?

Any help on this would be greatly appreciated. If you need anymore info, please let me know.

(if this is posted in the wrong subforum, I apologize and ofcourse you're free to move it when necessary)

---

### Post by Theimon on 2006-08-20
*Bump*

---

### Post by randell6564 on 2006-08-20
> **Theimon said:**
> 
    
Ubuntu doesn't recognize it's a SATA device? So maybe that's why I can't seem to find a way to enable DMA or the 32-bits IO support?





There is not much support yet for S-ATA Raid devices.

Check this out [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

---

### Post by Theimon on 2006-08-21
Ah thank you for the link. A big load of info will keep me quiet for a while ;)
Cheers.

---

