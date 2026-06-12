---
title: "Dell Latitude E5420/i5-2520M"
date: 2013-06-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mathew.chacko on 2013-06-29
I got into a strage situation, got one Dell Latitude E5420/i5-2520M/4Gb/500Gb/Bios A01/Win7 64Bit to install Ubuntu. So I tied 13.04 64Bit as dual boot. 
The laptop config looks similar - [http://wiki.yobi.be/wiki/Laptop_Dell_Latitude_E5420](http://wiki.yobi.be/wiki/Laptop_Dell_Latitude_E5420)

At first all worked fine. after few minutes system hung. Restarted all worked fine. but time to time either touchpad or the power management was not working fine. I visited many post on this. I thought let me reproduce the touchpad issue. when I used 2 finger for few seconds, noticed that the touchpad is not working and the trackball is jumping with AC power (smooth with battery).

Checked Dell support page for BIOS update and found that 2 updates are available. Thought the problem could be of this. so applied A02 and the A03. Was happy and expecting all will be fine. BUT BIG NO. The Latidude is not Booting to Ubuntu 13.04 (64bit) but from grub boots to Windows 7 (64bit).

Tried live USB 13.04 (64bit) and 12.04.2 (64bit) and live CD 13.04 (64bit) but no success. Not booting after selection "Try Ubuntu" nor "Install Ubuntu"

Any suggestion?

Thanks in advance. Mat.

---

### Post by mathew.chacko on 2013-06-30
SOLVED. In BIOS ver.A03, under System Configuration - Integrated NIC, the setting changed to "Enabled w/PXE" from "Enabled" and started working.

---

