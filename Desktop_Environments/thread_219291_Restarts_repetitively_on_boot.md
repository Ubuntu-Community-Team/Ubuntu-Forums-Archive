---
title: "Restarts repetitively on boot"
date: 2006-07-19
forum: Desktop Environments
---

### Post by cryburn on 2006-07-19
Hi,

I'm new to ubuntu. I've just installed it on a fairly old laptop, which all seemed to go fine. Now though when I try to start it up it has the following (copied from a pic i took so sorry bout any errors):

Booting 'Ubutu, kernel 2.6.15-23-server'

root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.15-23-server root=/dev/hda2 ro quite irqpoll
 [linux-bzimage. setup=0x1c00, size=0x16b75f]
initrd /boot/initrd.img-2.6.15-23-server
 [linux-initr @ 0x2900000, 0x69f638 bytes]
savedefault
boot

Then it restarts and does the whole lot again and again. I have tryed booting in recovery mode, but it doesn't work either.

I can't see anything about this problem anywhere in this forum - any help would be much appreciated!

Laptop specs are:

toshiba 430cdt
120mhz
48MB RAM
1.4G hdd - 400mb swap space.

I know this is an old machine, but if at all possible i'd like to get it running as a trial LAMP server.

---

### Post by krismatth3 on 2006-07-19
Can you try Damn Small Linux on it? [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) (livecd)

That might be more appropriate for such a system, and it can be easily installed to the hard disk if you decide to do so.

---

### Post by kinematic on 2006-07-19
or maybe puppy linux.
those specs are really way to low to run ubuntu in a decent way.

---

### Post by cryburn on 2006-07-19
Thanks - I'll give it a go. I know this is an ubuntu forum but any suggestions on what to run on DSL to configure an easy LAMP server.

---

