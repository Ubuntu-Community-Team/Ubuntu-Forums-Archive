---
title: "cdrom mounts to /dev/hda instead of /dev/hdc"
date: 2005-12-28
forum: Desktop Environments
---

### Post by girionis on 2005-12-28
Hello, my cdrom used to mount to /dev/hdc (/media/cdrom) but now it mounts to /dev/hda (/media/cdrecorder) after I tried to enable dma automatically (I changed the hdparm.conf file). It's not a problem mounting to /dev/hda but a) I have some scripts that already use /dev/hdc and b) I would like to know what exactly happened and it mounts to /dev/hda. I got the old hdparm.conf back but with no luck.

Whan I try to mount the cdrom I get:

$ mount /media/cdrom
mount: special device /dev/hdc does not exist


Thak you for your help.

---

### Post by sciurus on 2005-12-28
What drives do you have in your computer, and what IDE channels are they connected to in what order?

---

### Post by girionis on 2005-12-28
Hello,

I have only one IDE drive, my DVD rom (my hard drive is SATA), which is connected to IDE2 channel (I followed the instructions of my motherboard's manual).

---

### Post by dcstar on 2005-12-28
[QUOTE=girionis]Hello,

I have only one IDE drive, my DVD rom (my hard drive is SATA), which is connected to IDE2 channel (I followed the instructions of my motherboard's manual).[/QUOTE]
hda is the Master IDE device on the first IDE channel that Ubuntu detects, hdb is the Slave device. hdc is the Master on the second IDE channel, hdd the Slave.

I would imagine that you disabled the Primary IDE channel in your BIOS (since you don't use it......), so now Ubuntu only sees your Secondary Channel that your DVD-ROM is connected to.

Try re-enabling your unused IDE channel.

---

