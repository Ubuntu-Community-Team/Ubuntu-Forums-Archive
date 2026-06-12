---
title: "Network &amp; CD mount problems - Inspiron 8000"
date: 2008-06-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Star-Strewn on 2008-06-03
Hope I'm posting this in the correct forum.

Since I successfully installed Xubuntu 8.04 on my old Inspiron 8000 laptop, a few problems have cropped up.  Any help would really be appreciated, with internet access being the critical issue.

#1) Xubuntu's installer could not find an ethernet device, even though there is a port right on the side of the laptop.  Is there any way to manually configure the ethernet, or can it be detected some other way?

#2) I'm trying to use a wireless PCMIA card (Linksys WPC54G) instead.  After installing ndiswrapper, the card does NOT seem to work if inserted in the slot BEFORE boot.  However, I can connect to the network just fine if I insert the card AFTER Xubuntu's desktop has booted up.  How can I fix this so that I don't need to keep removing & reinserting the network card every reboot?  Also, how can I prevent Xubuntu from freezing when the card is removed?

#3) Every time I insert a CD, I get this error message:
```
**Failed to mount "New Volume".**
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0
```
The CD ends up working fine, but how do I stop that error from popping up?

I thought installing a *ubuntu distribution would be relatively painless, but it seems that it manages to keep me on my toes.  :p

Again, any help would be appreciated.
Thanks!

---

### Post by him610 on 2008-06-04
Maybe we can figure some way to help; how about posting the results of this command.

$ lspci

---

### Post by Star-Strewn on 2008-06-04
Well, thanks to linuxwireless.org, I managed to get the wireless card working just as it should be by installing the Broadcom b43 driver.  :)

I'd still like to see if I could get the ethernet working, although it's not really a *necessity *now that the wireless is good.

The output of lspci is:
```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M4 AGP
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 Communication controller: Agere Systems WinModem 56k (rev 01)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
07:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

In addition to the automatic CD mount error I described above, I am now getting an error every time Xubuntu boots up.  It tells me I need to search for the correct codec... however, after attempting the search, it tells me no appropriate codec can be found.  As far as I know, there is no media set to play upon startup, so this message seems really bizzare to me.

---

### Post by him610 on 2008-06-05
The listing from lspci does not indicate a network controller installed. It does indicate you have a modem installed...

```
02:06.0 Communication controller: Agere Systems WinModem 56k (rev 01)
```

and your wireless internet card...

```
07:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

I think I would forget about a wired connection since you succeeded in getting the wireless working.

Don't think I can help with your with your other problems though. I use some fairly old hardware myself, and normally, the older hardware works quite well when using Ubuntu.

Good luck.

---

### Post by Star-Strewn on 2008-06-06
Odd that there is no ethernet controller listed, but I agree, I shouldn't worry now that wireless is fine.

I managed to get rid of the mount error message when inserting CDs, by going to Xubuntu's Removable Drives & Media options and unchecking both "mount removable media when inserted" and "mount removable drives when hot-plugged".  The CD can still be navigated and the icon shows up on the desktop when inserted, so it seems the system was trying to automatically mount the drive *twice* for some reason.  However, the drawback to this workaround is that the "browse removable media when inserted" option no longer functions.  It seems there could be a better solution.

There has to be a way to identify what is causing the "Search for suitable codec" dialog to appear every boot-up.  How would I look into this (by logs and/or checking exactly what starts on boot)?  I'm new to Linux, so I don't know all the conventions of the system yet.

Thanks

---

### Post by Star-Strewn on 2008-06-06
I managed to chat live with a self-professed Linux nerd, and we ended up just disabling the 'which gnome-codec-install' command that called that window.  I already downloaded the major audio/video codecs.  And if I need to update codecs, there is always apt-get.

Thanks for the assistance!  :)

---

