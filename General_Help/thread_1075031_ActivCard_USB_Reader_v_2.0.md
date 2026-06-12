---
title: "ActivCard USB Reader v 2.0"
date: 2009-02-19
forum: General Help
---

### Post by Lachlanus on 2009-02-19
Hi, I'm new to having a Linux box at home.  I wanted to try it out to stick it to the man, and also because I hear it's more stable and less diseased than Windows.  A complete conversion, however, depends on my ability to get all the things I need to run.  I need to hook up to my works VPN which requires a CAC (smart card) reader.  I have read many articles about getting them to work.  The first step seems to be updating the firmware.  I have run (in WinXP) SCR3xxx_installer_V8.18, and then the FW update utility; however, every time I try, it tells me "no scm usb device found."  Is this a problem anyone else has come across?  In this article ([http://symbolik.wordpress.com/2007/02/26/scm-scr-331-usb-smartcard-reader-firmware-upgrade/](http://symbolik.wordpress.com/2007/02/26/scm-scr-331-usb-smartcard-reader-firmware-upgrade/)) it seems to indicate this should only happen if the first program isn't run.

---

### Post by Lachlanus on 2009-02-21
bump for help please

---

### Post by Lachlanus on 2009-02-24
bump for help please.  These readers are supposed to work, or so the legend goes...

---

### Post by James_in_Utah on 2010-02-23
I am also having trouble getting an ActivCard Reader 2.0 to work.  When I enter "lsusb", I see the reader listed:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 091e:0003 Garmin International GPSmap (various models)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[COLOR=Red]Bus 002 Device 010: ID 09c3:0008 ActivCard, Inc. SmartCard Reader[/COLOR]
Bus 002 Device 009: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 002 Device 006: ID 03f0:4811 Hewlett-Packard PSC 1600
Bus 002 Device 004: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I've followed the directions in several threads regarding getting a CAC reader to work.  The first problem I hit is the pcsc_scan doesn't pick it up.  It just hangs up with the following:

PC/SC device scanner
V 1.4.15 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.102
Scanning present readers...
Waiting for the first reader...

Any help getting this resolved would be greatly appreciated!
Thanks,
James

---

### Post by cham93086 on 2010-02-28
I can't give you a full solution, mine just stopped working (I'm trying to track down the culprit now!) but to start, you need to update your firmware. the following link has a link to the updating utility, you need to do this from a windows computer, with activegold (the windows middleware) installed.  <<http://www.txsystems.com/downloads/SCRx31CCID_fw5.22.zip>>  Once that is done, you will need to install coolkey, pcsc-tool and pcscd by  
```
sudo apt-get install coolkey pscsd pcsc-tools
```.
after that, I'm as stuck as you, I'll update If I get mine working again.

---

### Post by rlh1919 on 2010-03-26
> **cham93086 said:**
> I can't give you a full solution, mine just stopped working (I'm trying to track down the culprit now!) but to start, you need to update your firmware. the following link has a link to the updating utility, you need to do this from a windows computer, with activegold (the windows middleware) installed.  <<http://www.txsystems.com/downloads/SCRx31CCID_fw5.22.zip>>  Once that is done, you will need to install coolkey, pcsc-tool and pcscd by  
```
sudo apt-get install coolkey pscsd pcsc-tools
```.
after that, I'm as stuck as you, I'll update If I get mine working again.

Anybody ever find a fix for this? Get it working? I tried to flash the device with firmware but there is no current firmware for it from SCM website [http://www.scmmicro.com/support/pc-security-support/downloads.html](http://www.scmmicro.com/support/pc-security-support/downloads.html)
Have followed these instructions with no luck [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

---

### Post by spaznrq on 2010-12-10
> **rlh1919 said:**
> Anybody ever find a fix for this? Get it working? I tried to flash the device with firmware but there is no current firmware for it from SCM website [http://www.scmmicro.com/support/pc-security-support/downloads.html](http://www.scmmicro.com/support/pc-security-support/downloads.html)
Have followed these instructions with no luck [https://help.ubuntu.com/community/CommonAccessCard](https://help.ubuntu.com/community/CommonAccessCard)

I'm not sure if anything has changed since you posted, but I was able to get my CAC reader working in 10.10 following this article to update the firmware: [http://www.fantaghost.com/2010/07/upgrade-activcard-reader-v-2-firmware-scr-331-usb/](http://www.fantaghost.com/2010/07/upgrade-activcard-reader-v-2-firmware-scr-331-usb/)

Then I just followed that Ubuntu community help page for the CAC and things worked.  Got it working for Firefox and Thunderbird for email as well.

---

