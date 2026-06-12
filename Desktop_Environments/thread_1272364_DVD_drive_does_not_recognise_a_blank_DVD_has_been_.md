---
title: "DVD drive does not recognise a blank DVD has been inserted"
date: 2009-09-22
forum: Desktop Environments
---

### Post by pdc on 2009-09-22
Problem: if I insert a blank DVD +R disc into the DVD drive, there is much whirring but the DVD creator does not open up; (whereas if I insert a CD it will open this programme); I am running linux mint that is based on ubuntu;

I think this started about a week ago: I am sure I did burn a DVD or two on this computer a month or so ago; I have not installed any upgrades recently;

gedit etc/fstab gives

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=079a9e41-a9f5-4db3-a64a-d84a7b9cf8ba /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=8659447c-9bb9-4a5c-bcc3-6500df547dbc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

grateful for any help: the drive will boot a DVD

---

### Post by majiciannz on 2009-09-22
> **pdc said:**
> Problem: if I insert a blank DVD +R disc into the DVD drive, there is much whirring but the DVD creator does not open up; (whereas if I insert a CD it will open this programme); I am running linux mint that is based on ubuntu;

I think this started about a week ago: I am sure I did burn a DVD or two on this computer a month or so ago; I have not installed any upgrades recently;

gedit etc/fstab gives



grateful for any help: the drive will boot a DVD
I have a similar problem but with blank DVD+RW.
Won't mount or show an icon on the desktop.
However, I am still able to burn an iso image to disk.

Blank DVD-R and blank CD both mount an icon on the desktop.

I have not been able to find a fix for this as yet.
Hope you have better luck.

---

### Post by pdc on 2009-09-29
when I type in the command

> tail -f /var/log/messages enter

and then put a blank CD in our DVD drive I get the message

>  pdc-desktop kernel: [16201.461808] cdrom: This disc doesn't have any tracks I recognize!

and it opens the CD/DVD creator programme in gnome

when I enter a blank DVD I get much whirring, and no record from the above

........ when I try the same in an OpenSuse version, I get the reply

>  desktop kernel: cdrom: This disc doesn't have any tracks I recognize!

to both a blank CD; and a blank DVD;

and to both, I get a prompt to as to what type of CD or DVD I would like to create .........

....... I wonder what happens if other Ubuntu users insert a blank DVD:

if they firstly type 

> tail -f /var/log/messages in a terminal and look for the results

---

