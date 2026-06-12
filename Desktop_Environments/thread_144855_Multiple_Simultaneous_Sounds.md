---
title: "Multiple Simultaneous Sounds"
date: 2006-03-15
forum: Desktop Environments
---

### Post by chazzy on 2006-03-15
Hi there,

On the dreaded windows, I was able to be listening to Winamp and now and again another sound would play as required such as an IM message, or windows sound etc.

On Linux however, I play music and it takes total ownership of the sound card and doesnt let anything else play. If a system sound cuts in between tracks, xmms dies screaming that it cant find a sound card.

Does anyone know if this is possible? :/

Cheers.

I'm using an onboard AC97 sound device which was picked up etc no problem and installed. 

root@sphinxtu:/windows# lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS]: Unknown device 0181 (rev 01)
0000:00:08.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)

---

### Post by Stemp on 2006-03-15
May be [http://ubuntuforums.org/showthread.php?t=26567](http://ubuntuforums.org/showthread.php?t=26567)

---

### Post by kaamos on 2006-03-15
For me it helped just to install alsa-oss and change all programs to use alsa. Everything works at the same time except skype and realplayer.

---

