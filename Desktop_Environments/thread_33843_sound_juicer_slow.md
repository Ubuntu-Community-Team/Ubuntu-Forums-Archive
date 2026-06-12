---
title: "sound juicer slow"
date: 2005-05-12
forum: Desktop Environments
---

### Post by fng on 2005-05-12
Why is sound juicer (tried goobox 2) so slow in ripping cd's compared to iTunes?
He's ripping here with a max speed of 1.5x.

---

### Post by Dax0r on 2005-05-12
Dma is enabled?

---

### Post by mrtaber on 2005-05-12
I ran into the same thing; do a forum search (on cd-rom, dma)--you'll find out how to check to see if your DMA is active on your CD-ROM drive;  well, heck, just type

```
sudo hdparm /dev/hdc
``` (or hda or whatever the device name is of your cd-rom).

If DMA is not active, you'll have to activate it.  This will probably entail changes to the hdparm.conf file as well as the modules file.  I'm now ripping and encoding (FLAC) at speeds averaging around 7x (between 5x and 12x, depending on the CD--I have lots of old ones).

You can also turn off paranoia for your ripping, but that's something that I don't recommend...you tend to end up with more audio artifacts without cdparanoia while ripping.  But that's another forum search :)

Good luck,
Mark :)

---

### Post by fng on 2005-05-12
```
fng@butters:~$ sudo hdparm -d /dev/hdb

/dev/hdb:
 using_dma    =  1 (on)
fng@butters:~$
```

---

