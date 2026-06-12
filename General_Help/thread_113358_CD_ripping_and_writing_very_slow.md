---
title: "CD ripping and writing very slow ?"
date: 2006-01-06
forum: General Help
---

### Post by petef on 2006-01-06
Hi guys,

Tried ripping in sound juicer and terminal but a CD takes about 30mins to rip ? I only seem to get speeds of about 1x ? I have enabled DMA etc. Writing using Serpentine is also very slow. 

Please help as I need to rip and write quite a few CD's

Cheers

Pete :)

---

### Post by petef on 2006-01-06
Anyone ?

Pete

---

### Post by starNIX on 2006-04-24
same here.  I'm assuming it is prolly a gstreamer issue.  I am gonna look into it and see what I come up with.

---

### Post by joshrobinson on 2006-04-24
[QUOTE=starNIX]same here.  I'm assuming it is prolly a gstreamer issue.  I am gonna look into it and see what I come up with.[/QUOTE]

i would double check that dma is def activated.. for some reason it was turning it off on me when i rebooted even though i edited the files

```
/sbin/hdparm /dev/hda
```
asuming your cdrom is hda

```
/sbin/hdparm -d1 /dev/hda
```
to turn dma on hda until reboot

oh yeah and

```
gedit /etc/hdparm.conf
```

to edit the hdparm files to make dma always stay on.. but for some reason mine keeps shutting off

---

### Post by silentb on 2006-05-26
Disabling all error correction usually helps to speed up reading to 10x - 20x. In KDE see  System settings -> Sound and multimedia -> Audio CDs. In other programs disable all kinds of "cdparanoia".

---

