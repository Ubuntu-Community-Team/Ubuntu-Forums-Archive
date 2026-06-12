---
title: "automatrix dma problem"
date: 2006-02-09
forum: Desktop Environments
---

### Post by shovex on 2006-02-09
ok i installed automatrix and enabled dma for the cdrom .. so now when i go to read a burned cd i burned on windows, i can't read the cd ..  and it only started happening after i enabled dma. so how do i remove the dma option? :p

---

### Post by o_fortuna on 2006-02-09
[QUOTE=shovex]ok i installed automatrix and enabled dma for the cdrom .. so now when i go to read a burned cd i burned on windows, i can't read the cd ..  and it only started happening after i enabled dma. so how do i remove the dma option? :p[/QUOTE]
You need to restore your hdparm.conf file (which Automatix backed up). Just open a terminal (Applications-->Accessories-->Terminal) and copy this in and press enter:
```
sudo cp /etc/hdparm.conf_backup /etc/hdparm.conf
```
That should put it back to normal.
You could also do this:
```
sudo gedit /etc/hdparm.conf
```
and get rid of the line near the very bottom that says something like DMA=on. The first way is probably better, though.

---

