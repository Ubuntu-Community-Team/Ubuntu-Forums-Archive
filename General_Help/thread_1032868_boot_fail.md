---
title: "boot fail"
date: 2009-01-06
forum: General Help
---

### Post by unrelatedwaffle on 2009-01-06
I installed kubuntu via Wubi on my Asus M50VM so I could dual-boot Kubuntu and Vista, but when I try to boot into kubuntu after install, an error message too quick to read flashes and there's a loud, alarming beeping noise. I then get the following screen:


Booting Ubuntu 8.10 kernel 2.6.27-7-generic

Filesystem type is ntfs, partition type 0x07

The current working directory (i.e., the relative path) is /ubuntu/disks [Linux-bzImage, setup=0x3000, size=0x238180]
[Linux-initrd@0x7f76f000, 0x880263 bytes]

mount: cannot setup loop device: No such file or directory
mount: mounting root/dev on /dev/.static/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/itit
No init found. Try passing init=bootarg.


Then the "type help for a list of commands" dialogue comes up. . .How can I reboot from this screen without doing a hard shutdown, by the way? None of the commands look familiar to me. Would installing from a LiveCD be a better idea?

---

### Post by caljohnsmith on 2009-01-06
> **unrelatedwaffle said:**
> Would installing from a LiveCD be a better idea?
Considering your problems with Wubi, I think giving Kubuntu its own partition and doing a standard dual boot install via the Live CD is a good plan. That's just my 2 cents though. :)

---

### Post by Zeroberry on 2009-01-06
sudo shutdown now

---

### Post by unrelatedwaffle on 2009-01-08
Well, I tried just running the liveCD, and I got even crazier things this time. The first time I tried, I got that quick flashing error. The first line is "Expecting a Reference Packet Element" and the second line went away before I could memorize it. The screen then went completely black and I couldn't do anything except hard restart. 

I tried the same process so I could write down the second part of the error, but this time kubuntu started to load, and got all the way through the blue status bar before the screen flashed black and then I got a screwy green and tiled screen of the kubuntu logo, again completely frozed. 

The third time I tried "check this CD for errors," and after running its test, the screen went completely black and did nothing. 

I'm about ready to give up. I googled "expecting a reference packet element" and got zero hits.

---

