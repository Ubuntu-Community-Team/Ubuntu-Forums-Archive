---
title: "How to Mount DVD drive when running live session from USB"
date: 2014-10-08
forum: Desktop Environments
---

### Post by futureal2032 on 2014-10-08
Hi all,

I use Ubuntu Gnome 14.01 LTS in live session and I use it from a USB pen drive on my Desktop..

My question is..

[B]When I run live session from a USB Pendrive...
How do I use my SATA DVD Writer?[/B]
 I mean under "Disks" it shows me the DVD Writer..but it does not mount..
**So how do I mount the DVD writer and use it to burn CD's/DVD's?**

---

### Post by Impavidus on 2014-10-09
You can't mount dvd writers. You can mount a dvd located in that writer, or more precisely said a file system on that dvd, but not a blank dvd or the writer itself. To burn a dvd, insert a blank dvd, open the burn program and burn it. I don't know which if any burn tool is installed by default on the live disk. On my installed system I have xfburn, which comes by default on Xubuntu.

---

### Post by mitchd123 on 2014-10-09
Find your dvd by doing a listing of the devices with a command like ls /dev/dvd* or ls /dev/cdrom*


To burn a dvd you could burn an iso with something like:
growisofs -dvd-compat -Z  /dev/dvd=/root/dvd.iso

or

growisofs -Z /dev/dvd1 -R -J -dvd-compat ./*

If growisofs is not on the liveusb,  then install it for the session with sudo apt-get install growisofs

---

