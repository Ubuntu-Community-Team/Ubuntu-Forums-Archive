---
title: "Photorec File Recovery - Segmentation Fault"
date: 2009-04-26
forum: General Help
---

### Post by afrodeity on 2009-04-26
I'm trying to recover data from a second SATA drive. I have about 60GB free on my main drive, but have run into a "segmentation error" which stopped the recovery process. Any ideas? Also, photorec doesn't appear to recover .doc files. Is there a way of restarting the process from the sector where it stopped? Thanks.


```
 PhotoRec 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 500 GB / 465 GiB (RO)
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 60800 254 63  976768002 [Gaia]


Pass 1 - Reading sector  749520232/976768002, 461038 files found
Elapsed time 4h58m47s - Estimated time for achievement 1h30m35
txt: 390571 recovered
tx?: 22106 recovered
png: 8417 recovered
jpg: 7371 recovered
gz: 6855 recovered
tif: 5976 recovered
gif: 4851 recovered
elf: 3332 recovered
cab: 2952 recovered
mp3: 1879 recovered
others: 6728 recovered
Segmentation fault
afrodeity@afrodeity-desktop:~$ 
```

---

### Post by flyingmayo on 2009-08-06
ditto

---

### Post by michy99 on 2009-08-06
To recover files not supported by photorec, try ext3grep. It is also useful for recovering specific files if you know the path where the file was at.

---

### Post by Hobgoblin on 2009-08-06
> **afrodeity said:**
> Also, photorec doesn't appear to recover .doc files.

It [should](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec).

Did you go through all the screens of file types?

---

