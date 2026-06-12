---
title: "Problem TVtime Television viewer,how to run tv in ubuntu"
date: 2009-06-06
forum: General Help
---

### Post by tosunbd on 2009-06-06
Is it possible to run tv in ubuntu?
Application>Sound & Video>TVtime

Attached.:p

---

### Post by Sidewinder1 on 2009-06-06
Although the following thread deals mostly with the Hauppague HVR 950Q, it should certainly get you headed in the right direction. Oh, BTW, the answer to your question is obviously yes. :-)
[http://ubuntuforums.org/showthread.php?t=1021901&highlight=HVR+950Q](http://ubuntuforums.org/showthread.php?t=1021901&highlight=HVR+950Q)

HTH,
Side

---

### Post by tosunbd on 2009-06-06
> **Sidewinder1 said:**
> Although the following thread deals mostly with the Hauppague HVR 950Q, it should certainly get you headed in the right direction. Oh, BTW, the answer to your question is obviously yes. :-)
[http://ubuntuforums.org/showthread.php?t=1021901&highlight=HVR+950Q](http://ubuntuforums.org/showthread.php?t=1021901&highlight=HVR+950Q)

HTH,
Side
Hello 
Is there any command to know about my TV-Card?

---

### Post by Sidewinder1 on 2009-06-06
Is it an actual internal card or a USB device? What make and model?

---

### Post by tosunbd on 2009-06-06
> **Sidewinder1 said:**
> Is it an actual internal card or a USB device? What make and model?
External TV-Card.AverMedia:)

---

### Post by Sidewinder1 on 2009-06-06
If it's an internal card, open a terminal and type:
```
lspci
```
If it's a USB, type in terminal:
```
lsusb
```
and you should see it listed if it's being detected.
If detected and not working you may need to install firmware, and/or drivers and/or reinstall or configure Tvtime. Failing the above, Kaffine (sp?) and Mythtv are also options if for some reason Tvtime is incompatable.

HTH,
Side

---

### Post by tosunbd on 2009-06-06
> **Sidewinder1 said:**
> If it's an internal card, open a terminal and type:
```
lspci
```If it's a USB, type in terminal:
```
lsusb
```and you should see it listed if it's being detected.
If detected and not working you may need to install firmware, and/or drivers and/or reinstall or configure Tvtime. Failing the above, Kaffine (sp?) and Mythtv are also options if for some reason Tvtime is incompatable.

HTH,
Side
Sorry,It may be internal.
lspci
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:02.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

```
lsusb
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
It is attached with motherboard like graphics-card.

---

### Post by Sidewinder1 on 2009-06-06
04:02.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1

I "think" the above is it but I'm not sure. You're going to need someone more knowlegable than I to get this working. Might I 
suggest that you create a new post in the forum that I have listed below?

---

### Post by Sidewinder1 on 2009-06-06
[http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

---

