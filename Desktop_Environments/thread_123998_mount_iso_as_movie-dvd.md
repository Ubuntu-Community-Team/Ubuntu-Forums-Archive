---
title: "mount iso as movie-dvd"
date: 2006-01-31
forum: Desktop Environments
---

### Post by maxdevis on 2006-01-31
how can i mount an iso, so i can click in xine or vlc the dvd-button?

---

### Post by lapsey on 2006-01-31
I was working on this for inclusion in a launcher..

> gksudo mkdir /media/iso ; gksudo modprobe loop ; gksudo mount file.iso /media/iso/ -t iso9660 -o loop ; nautilus --browser /media/iso

I'm quite new to all this so I am sure it doesnt work very well yet

---

### Post by taurus on 2006-01-31
sudo mkdir /mnt/iso
sudo mount -t iso9660 -o loop <filename>.iso /mnt/iso
xine dvd:/mnt/iso

---

### Post by maxdevis on 2006-02-01
you don't have to mount an iso
:D 

gxine dvd://%M  (%M=path to iso)

---

