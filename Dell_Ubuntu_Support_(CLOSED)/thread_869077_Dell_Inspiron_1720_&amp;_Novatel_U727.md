---
title: "Dell Inspiron 1720 &amp; Novatel U727"
date: 2008-07-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kurupt4 on 2008-07-24
Hello all, I am very new (very new!) to Ubuntu, I have been figuring things out real good, EXCEPT I cannot get my Novatel U727 air card to work. Can someone please guide me on this? I have spent at least 4 hours trying. I am running a Dell 1720 which came with Vista (SUCKS!!) and I have since reformatted the entire hd and installed Ubuntu Desktop 8.04.
Thank you in advance for you time and help.

---

### Post by StewartM on 2008-07-30
> **Kurupt4 said:**
> Hello all, I am very new (very new!) to Ubuntu, I have been figuring things out real good, EXCEPT I cannot get my Novatel U727 air card to work. Can someone please guide me on this? I have spent at least 4 hours trying. I am running a Dell 1720 which came with Vista (SUCKS!!) and I have since reformatted the entire hd and installed Ubuntu Desktop 8.04.
Thank you in advance for you time and help.


I just upgraded from Gutsy to Hardy, and I hit the same problem (it had previously worked on Gutsy). You can read about my experience there:

[http://ubuntuforums.org/showthread.php?t=875028](http://ubuntuforums.org/showthread.php?t=875028)

Can anyone verify that this is a bug?

StewartM

---

### Post by StewartM on 2008-07-31
> **Kurupt4 said:**
> Hello all, I am very new (very new!) to Ubuntu, I have been figuring things out real good, EXCEPT I cannot get my Novatel U727 air card to work. Can someone please guide me on this? I have spent at least 4 hours trying. I am running a Dell 1720 which came with Vista (SUCKS!!) and I have since reformatted the entire hd and installed Ubuntu Desktop 8.04.
Thank you in advance for you time and help.

Well, I've now successfully resolved my problem, are you still having problems? I'm not an "expert" but following the instructions at [www.sprint.com/downloads](www.sprint.com/downloads) worked for me.

Quick caveat: if the aircard pops up as a CD emblem when you mount it, "eject" it and it will remount automatically as a USB drive--which is what you want. Then proceed with the commands:

sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x1410 product=0x4100
sudo dmesg|grep -i ttyusb

Then start KPPP (configured as per the instructions) and it should go.

StewartM

---

### Post by rkeyzer on 2009-07-01
I used the driver from Inspiron 1525 and it worked for me.

---

### Post by macheted01 on 2009-10-08
Quote
Well, I've now successfully resolved my problem, are you still having problems? I'm not an "expert" but following the instructions at [[COLOR=#444444]www.sprint.com/downloads[/COLOR]]("http://www.sprint.com/downloads") worked for me.

Quick caveat: if the aircard pops up as a CD emblem when you mount it, "eject" it and it will remount automatically as a USB drive--which is what you want. Then proceed with the commands:

sudo modprobe -r usbserial
sudo modprobe usbserial vendor=0x1410 product=0x4100
sudo dmesg|grep -i ttyusb

Then start KPPP (configured as per the instructions) and it should go.

StewartM
 
 
I have no idea what I am doing on trying to get my U727 to work on Ubuntu.
Where do you enter the commands at?

---

