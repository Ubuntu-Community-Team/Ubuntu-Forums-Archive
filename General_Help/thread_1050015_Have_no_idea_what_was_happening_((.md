---
title: "Have no idea what was happening :(("
date: 2009-01-25
forum: General Help
---

### Post by illdemon on 2009-01-25
Well that was a very beautiful afternoon, i was playing around with compiz, evrything seems to work fine: cube, tranparent windows.., but BOOP!! everything gone, when i see the system>pref>effect it turned to none automatically, then i click on the normal or extra, it show the keep or don't keep settings window, i clicked keep and .. nothing changed: no effect at all. when i go back to the sys>pref>effct it turned to none again:( now i am hopless can smb help me??????????
Here are the results for some commands
-glxinfo | grep direct >>>
  + If i start terminal with key bindding then : direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
  + If i start terminal with gnome pannel then : direct rendering: Yes
-lspci >>> 
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
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
 
-My computer have no xsever-xgl installed
-here is my xorg.conf
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by 73ckn797 on 2009-01-25
I assume you tried to reboot. Could be that the changes won't take effect until then. Sort of like when you install restricted video drivers.

---

### Post by illdemon on 2009-01-25
I did'nt install anything and i tried to restart manytimes :(
Thanks for the advice.

---

### Post by 73ckn797 on 2009-01-26
You will have to "bump" this thread. I do not think I can help. I quite using all of the eye candy stuff.

---

