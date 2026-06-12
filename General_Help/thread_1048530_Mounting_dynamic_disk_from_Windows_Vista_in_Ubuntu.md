---
title: "Mounting dynamic disk from Windows Vista in Ubuntu"
date: 2009-01-23
forum: General Help
---

### Post by kovariadam on 2009-01-23
Hello,
i need to mount partitions of dynamic disk created in Vista containing 2 partitions one for mirror and one for stripping RAID. Ubuntu can see only one partition which is the whole disk and it can't mount it since it actualy contains 2 partitions.

I'm using Ubuntu 8.10 x86_64.

Is there any way to accomplish this?

Thanks in advance
Adam Kovari

---

### Post by fjgaude on 2009-01-23
Have you looked into a program called **dmraid**? That should permit you to mount Windows raid partitions. Get it using:

```
sudo apt-get intall dmraid
```

After read the **man** pages for it.

---

### Post by kovariadam on 2009-01-23
Thank you fjgaude,
i tried the dmraid program, but it doesn't seem to work with windows dynamic disk manager created partitions.
> 
adam@adam-ubuntu:~$ sudo dmraid -l
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,10)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs

I might be wrong, which of these types am i supposed to use?, dos? If so, then why dmraid sees no raid partitions?
> 
adam@adam-ubuntu:~$ sudo dmraid -r
No RAID disks


Thanks for helping

---

