---
title: "Dell Restore CD to USB"
date: 2010-02-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by leighgable on 2010-02-04
Hello All,

I am trying to restore a dell A90 netbook with the contents of the restore CD shipped with the device. So far nothing will boot up, although I can boot from another USB pen drive with a standard liveCD on it.

I've tried using the techniques to make a bootable USB drive both with usb-creator and unetbootin. I've made iso copies of the contents of the disc with both cat and dd. 

If anyone can provide some help I would appreciate it greatly. Here are the contents of the disc:
```
A1341_UP.img
belmont-travel-stable-install-usb-20090108-1.img
boot.cat
bootfs.img
boot.msg
initrd0.img
install.cfg
install.sh
isolinux.bin
isolinux.cfg
liveusb-creator-ubuntu-installer-0.3.2.1.exe
logo.png
rootfs.img
vesamenu.c32
vmlinuz
```

---

### Post by nanotube on 2010-02-04
Hi,

Can't help you with the specific problem of trying to get a liveusb out of the dell restore cd, as I haven't done that myself...

But I will ask you: why do you even want to do that? Just about as soon as i got my A90, I tested out a standard ubuntu karmic on it, and once I figured out how to get all hardware to work, I installed the stock karmic on it.

There are a number of shortcomings in the 'dellbuntu' that comes preinstalled, so I strongly recommend an upgrade to stock ubuntu.

See my howto for getting all hardware to work here:
[http://ubuntuforums.org/showthread.php?t=1389877&highlight=a90](http://ubuntuforums.org/showthread.php?t=1389877&highlight=a90)

---

### Post by leighgable on 2010-02-04
Hello,

Thanks for your help and your answer. I may end up doing what you suggest. I was interested in the recovery disk because it's 8.04, and I've heard that the real time kernel on hardy is solid. I am using the netbook for real time audio processing.

If anyone has a clue how to get the restore CD working on a USB drive, that would be much appreciated.

In the meantime, I'll put Karmic on and see if I can get glitch free audio. 

Thanks,
Leigh

---

### Post by Zerocool Djx on 2010-02-08
When you installed Ubuntu it changed your master boot record (MBR) when that happend the PC restore startup protocol was erased.

Call Dell give them the windows certificate and they will mail you a copy (you already paid for it when you bought the system).

However, if you do manage to make a USB restore,.. I would LOVE to have a copy of it. seems like you have the files,.. you just got to make the USB bootable. Let me switch to windoes and see if my boot loader program supports this.. I'm kinda curious.. brb


On a side note, I am having audio problems as well on my E1505 with Karmic

---

### Post by leighgable on 2010-02-08
Hello,

I wasn't able to make an iso or disc image that was bootable from my usb drive. I ended up taking nanotube's advice and just going with a Karmic NBR install. If you want I can throw the iso I did get up on a fileshare service.

It's taken a fair amount of configuring, but I have a good truce now between Pulseaudio, Alsa, and Jack and a realtime kernel. If that's what you need, check out this post:

[http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/](http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/)

But, you'll also need to install an old package of alsa-utils inorder to get the alsa sound card chooser which is no longer included in the packages: copy the asoundconf from /usr/bin, apt-get update alsa-utils back to the karmic version, and then stick your copy of asoundconf back into /usr/bin.

All the best, Leigh

---

### Post by snowpine on 2010-02-08
Good decision to go with Karmic. Dellbuntu 8.04 doesn't come with a real-time kernel anyway. ;)

---

### Post by Zerocool Djx on 2010-02-08
> **leighgable said:**
> Hello,

But, you'll also need to install an old package of alsa-utils inorder to get the alsa sound card chooser which is no longer included in the packages: copy the asoundconf from /usr/bin, apt-get update alsa-utils back to the karmic version, and then stick your copy of asoundconf back into /usr/bin.



Where you talking about my sound problem?

---

### Post by leighgable on 2010-02-10
Yes, I threw that in there in case it was what you needed.

---

