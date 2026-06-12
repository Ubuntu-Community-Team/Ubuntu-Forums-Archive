---
title: "[SOLVED] Dell 1420n - no fresh install for you"
date: 2007-07-21
forum: Dell  Ubuntu Support
---

### Post by specker on 2007-07-21
Got a new Dell 1420n yesterday.  It was working pretty good out of the box so I decided to put it to the test with a fresh install of Feisty.  Ouch.  The Live cd won't even boot I just get 
[HTML]/bin/sh: can't access tty; job control turned off[/HTML]

So I tried the alternate install cd.  That works, I can install it.  However on boot X is broke.  I've tried installing the updated xserver-xorg-video-i810 package and adding "intel" to the driver section in xorg.conf.  Still nothing.

Anyone successfully done this yet?  I know it can be done, it came from Dell working.

EDIT:
I got most everything working better then it was from the factory.  Here is how I did it.
[http://ubuntuforums.org/showthread.php?t=509408]("http://ubuntuforums.org/showthread.php?t=509408")

---

### Post by tak.ack on 2007-07-21
I have got a 1420 (with Vista) and partitioned space for Ubuntu Feisty install. 

I've installed using alternate CD, as I had your problem. For the X-server to work change "nv" in the device of /etc/X11/xorg.conf section to "vesa" and restart gdm.


There are many problems though.

1. CD/DVD-RW drive not recognized (doesn't mount and no devices in /dev)
2. Broadcom Wireless card and ethernet controller don't work

So, I cannot install Envy or install Nvidia drivers.

I've tried the getting tg3 firmware, but still cannot get internet to work via network-manager.
Anyone can help getting cdrom recognized, or the internet?

All I can mount, and the only way to get files onto the 1420 is via USB drive or SD card.

Some logfiles here: [http://www.rgvn.com/ubuntu_on_1420/]("http://www.rgvn.com/ubuntu_on_1420/")

---

### Post by specker on 2007-07-21
The stumbling block right now is the Intel X3100 graphics.  It sounds like you might have the nvidia card in yours.  Dell must be sprinkling a little extra magic on these things during the install.  Right now I'm running MEPIS on it without to many issues (no sound).  You might want to try it. I tried 7.10 tribe 3 and it hangs during the install. I wish someone knew what Dell was doing to get this thing to run feisty.

---

### Post by LMP900 on 2007-07-21
Does Dell provide it's own Ubuntu 7.04 disc? If so, does a fresh install from that work?

---

### Post by tak.ack on 2007-07-21
Dell has a linux wiki i found via a google serch

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Factory_Installation_Details](http://linux.dell.com/wiki/index.php/Ubuntu_7.04#Factory_Installation_Details)

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages) lists the additional packages installed in the ubuntu versions..

it seems for me to install linux on a 1420, I'd need to install the 1420N's additional packages that add hardware support.

The intel video issue seems to be solved via: xserver-xorg-video-intel_1.9.94-1ubuntu3_i386.deb
However, there are no links to download it.

I'll update as a I know more...


UPDATE:

I figured out how to make cdrom recognizable. It's working for me now!

Do the following to get CDRom to recognize and for USB-drives and SD-cards to be automatically mounted:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/CD_media_not_recognized](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/CD_media_not_recognized)

UPDATE2:

With the fesity CD mounted, I was able to install ndiswrapper after setting up a build environment.
And with ndiswrapper...the wireless internet now works!

Still, no solutions for the ethernet controller.

---

### Post by Shay Stephens on 2007-07-21
Looks like my 1420N should be showing up Monday.  Is it possible to make an HDD image before doing anything and using that as a future restore disk?  How can I go about that?  Anyone know or can point to a how-to that works for them?

I take it they don't include a restore disk?

---

### Post by specker on 2007-07-22
Thanks for the good info.  Dell does ship an Ubuntu cd but it is just the standard disk you can download.  I believe they put a rescue partition on your hard drive so you can reinstall from that.  Unfortunately I wiped them all clean for my fresh install.  Whoops!

---

### Post by LMP900 on 2007-07-22
Thank you, **tak.ack**. I'll be receiving my Inspiron 1420N in a few weeks and those links will be very handy!

---

### Post by specker on 2007-07-22
I've downloaded all of those packages except for the tg3-dkms.  Can't seem to find that one anywhere.  I'm going to attempt to install those from command line when x breaks.  I'll report back.

---

### Post by specker on 2007-07-22
Well, I got it working.  xserver is fixed.  I installed anything with kernel in the name from the Dell wiki posted above.  Then removed xserver-xorg-video-i810 and installed the xserver package from this thread [http://ubuntuforums.org/showthread.php?t=494943&highlight=intel+x3100+video]("http://ubuntuforums.org/showthread.php?t=494943&highlight=intel+x3100+video")

Then added "intel" for the driver in xorg.conf.  And finally did a sudo dpkg-reconfigure -phigh xserver-xorg.

This is a rough version of what I did because I was just trying everything.  I'm going to try to recreate and get a clear step by step.

Thanks tak.ack for the help!

---

### Post by sciurus on 2007-07-22
If you can't boot from a live cd, please check if [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119255](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119255) describes your problem.

---

### Post by sciurus on 2007-07-22
I'm attaching Dell's restore scipts from my 1420N.The ones in scripts/chroot-scripts are run after the Ubuntu image is restored. Reviewing them should provide information on how to get all hardware working after a clean install.

---

### Post by WAB on 2007-08-01
Hi guys,

I'm waiting for my new 1420. Unfortunately, dell is not sealing n-series in my country, so i had to buy only an Vista-based system. 

When i have it, i'm going to in install a dual boot system, and i'm looking for a good thread describing how do that.

I saw here some links to required add-ons, i've downloaded them already.

Thanks a lot

---

