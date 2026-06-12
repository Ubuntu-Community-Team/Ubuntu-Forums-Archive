---
title: "New User Having Sound and WiFi problems"
date: 2008-08-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by setnetjer on 2008-08-14
I've been saying for awhile that I'm going to switch over to Linux since I absolutely despise Windows, and I don't have the money to even begin to think about investing in a Mac, so today out of "boredom" I finally decided to install Ubuntu (Hardy Heron/8.04) onto my computer as a dual boot with Windows.

Since Installing Ubuntu, I've lost sound and the use of WiFi.

My sound card driver is supposed to be for SIGMATEL STAC 92XX C-Major HD Audio.  I've tried finding drivers for the audio but have been unable to find a fix for the problem by using Google.

Also, I've lost the use of my WiFi card, though the LED on my laptop IS lit up.  Unfortunately, this leaves me unable to use the internet unless I'm actually plugged in, which as a college student, kind of cripples my ability to do homework wherever I'm needing to do it at the time.

The computer is a Dell Inspiron 1501 laptop that I've had for almost a year now.

As a reference, I'm attaching the results of the command "lspci -v" in case it will help someone help me figure out a fix for either, or both, of these problems.

Any help would be greatly appreciated, as I am horribly stumped.

---

### Post by superm1 on 2008-08-14
Your network card is supported by an alternative driver that will be entering Ubuntu 8.04 in the future:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

---

### Post by setnetjer on 2008-08-14
I d will try what is listed in your thread but first, how do I make a blacklist file?  Sorry if that is something "basic" but I'm still quite new to Linux so it may take me a bit to figure out how to do everything.

---

### Post by superm1 on 2008-08-14
just create the file using an editor using superuser rights, eg

```
sudo gedit /etc/modprobe.d/blacklist-b43
```

---

### Post by setnetjer on 2008-08-14
Alright, got sound back by doing what was suggested in your thread, but now not even the WiFi LED light is lighting up, and when I go in to configure my networks, it doesn't even have an entry for a wireless network.:confused:

---

### Post by drsaamah on 2008-08-14
Alright your wifi led problem is simple fix.  The first thing you need is to find out what version of the linux kernel you are using.  Open up a terminal and type:
```
uname -a
```
For example, my computer gives:
```
saam@dAlembert:~$ uname -a
Linux dAlembert 2.6.24-19-generic #1 SMP Fri Jul 11 21:01:46 UTC 2008 x86_64 GNU/Linux

```
So my kernel version "2.6.24-19-generic".  The next thing you want to do is install the proper library for your kernel version to fix the wifi led.  In the terminal type in:
```
sudo apt-get install linux-backports-modules-YOUR KERNEL VERSION

```
So back to my computer as an example this would be done as so:
```
sudo apt-get install linux-backports-modules-2.6.24-19-generic

```
This should fix the led.  Now the real problem is why your wifi isn't working.  I'm going to *guess* that maybe its turned off in your BIOS.  When you restart the computer, go to the BIOS and make sure the wifi is enabled.  If the Inspiron 1501 has a wireless switch to control the wifi and bluetooth make sure that setting is set off (or if you prefer it to be on, make sure the switch is actually turned on).
If this still doesn't fix the wifi in Ubuntu, then the OS isn't recognizing your wireless card for whatever reason.  Type into a terminal:
```
ifconfig
```
And make sure one of the outputs is "wlan0".  If that output isn't there when the wifi led is on, then Ubuntu isn't recognizing the card.  Either way post back on here and we can work through it from there.

---

### Post by phenest on 2008-09-06
> **superm1 said:**
> Your network card is supported by an alternative driver that will be entering Ubuntu 8.04 in the future:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

I tried 8.04.1 Live CD on my mums Inspiron 1501, but the drivers for the Broadcom wireless crash when I try them. Are they likely to work better after installing Ubuntu? I have an Intel 3945abg mini-pci card that I tried but neither XP nor Ubuntu seems to recognize it (although it does work in my Precision M90). To get the Intel card working, would a BIOS update help?

---

