---
title: "destop effects simlpy stoped working"
date: 2008-12-24
forum: General Help
---

### Post by chicity on 2008-12-24
hello everyone,
  ok so my desktop effects simply stopped working for an unknown reason.
i have the  ATI Technologies Inc RC410 [Radeon Xpress 200] so i tried activating the ati/amd proprietary fglrx driver. then it told me i had to reboot so i did and when i got to the login screen the screen was all black and i got a message from my monitor saying that the screen resolution was out of range so then i ran dpkg-reconfigure xserver-org and rebooted again
that got my screen working again but still no effects.  i have tried different things like envy and this [HTML]https://help.ubuntu.com/community/RadeonDriver[/HTML]   but no luck. any help will be greatly appreciated and thank you lots in advanced.


sergio@SDLPC:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:04.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
sergio@SDLPC:~$

---

### Post by Wartender on 2008-12-24
try compiz-check, and download compizconfig-settings-manager from synaptic, see if you can enable them from there.

---

### Post by chicity on 2008-12-25
hey WARTENDER thanks for the reply  but i also forgot to mention that i have also tried that here are my results for compiz-check


sergio@SDLPC:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RC410 [Radeon Xpress 200]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 


is there a way that i can change the screen resolution from the terminal at login.Because if there is  then maybe i could just activate the proprietary driver, reboot and then change the res. so that my monitor wont be out of range.

---

### Post by Wartender on 2008-12-25
you could try logging in to failsafe GNOME or terminal, in the terminal type gnome-display-properties to change your resolution

---

### Post by chicity on 2008-12-26
I tried your suggestion and it says "display cannot be opened "

---

