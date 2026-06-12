---
title: "Video will not work at all?"
date: 2009-05-19
forum: General Help
---

### Post by Zavie A. on 2009-05-19
So, heres a probably stupid question.

Every time I try to play any type of video, It will open and then close right after, no matter the video file type and no matter the video player.

I've downloaded the GStreamer plugins to play video, and still nothing, However early this morning I found that If I play music on any music player, the video will work :S

It's pretty annoying actually. does anyone know how I can fix this?

Thanks in advance :)

---

### Post by Concrete on 2009-05-19
Ok...

1. what video card do u have?
2. which video player u try?
3. What video formats is (.ts/mkv/avi/mpeg/flv..)?

---

### Post by Zavie A. on 2009-05-19
Well, I had the same problem with my old computer, and I'm not entirely sure what kind of video card I have. How would I find that out?

for video players, Ive tried the default GNOME video palyer, VLC, azurus, Mplayer, and Xine.

and for formats Ive tried, flv, mpeg, mp4, avi, mov, and wmv.

---

### Post by Concrete on 2009-05-19
Type in terminal

> lspci

and past here result.

---

### Post by Zavie A. on 2009-05-19
> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 RAID bus controller: Promise Technology, Inc. PDC20271 (FastTrak TX2000) (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)

there you go!

---

### Post by Concrete on 2009-05-19
U have integrated video card, _Intel Corporation 82865G_...

When u installing Ubuntu did u install some driver for video card?

---

### Post by Zavie A. on 2009-05-19
nopee.
I just did a regular installation...It didnt ask me about drivers.

---

### Post by Concrete on 2009-05-19
Oke...

When a video card is integrated, Ubuntu install whitout asking you. So driver is 100% installed and it for ur version of motherboard (and i sea that in ur result on last post).

Did u maybe upgrade ur ubuntu to 9.04 or u install fresh copy of 9.04?

---

### Post by fillintheblanks on 2009-05-19
would this be a good idea?

[http://ubuntuforums.org/showthread.php?t=1136738](http://ubuntuforums.org/showthread.php?t=1136738)

---

### Post by Zavie A. on 2009-05-19
no :( ...i put 9.04, on an empty harddrive.

---

### Post by Zavie A. on 2009-05-19
thanks!
I'll give those drivers a try :)
maybe they'll work...

---

### Post by Concrete on 2009-05-19
Try **SMPlayer** (u have in synpatic) and come back whit result...

---

### Post by fillintheblanks on 2009-05-19
or this.. seems to be a fairly common problem

[https://wiki.edubuntu.org/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.edubuntu.org/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by Zavie A. on 2009-05-19
Didn't work. :(
crap.

---

### Post by fillintheblanks on 2009-05-19
did you try reverting the jaunty xorg intel driver to version 2.4?

[https://wiki.edubuntu.org/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.edubuntu.org/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

