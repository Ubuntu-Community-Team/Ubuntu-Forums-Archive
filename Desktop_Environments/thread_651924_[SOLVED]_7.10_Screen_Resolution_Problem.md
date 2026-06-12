---
title: "[SOLVED] 7.10 Screen Resolution Problem"
date: 2007-12-28
forum: Desktop Environments
---

### Post by maphco on 2007-12-28
I'm not entirely sure if this shouldn't go into the newbie area, I just installed Linux for the first time :).  I've tried to google ou a solution for this, but all the code I've seen for the xorg.conf file is different from mine. I only have the options for the two lowest resolutions...

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation C51 [GeForce 6150 LE]"
	Driver		"nv"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"HP vs17"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [GeForce 6150 LE]"
	Monitor		"HP vs17"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Also, just for pure curiosity, what language is this code written in?

---

### Post by maphco on 2007-12-28
Any help? :(

---

### Post by overdrank on 2007-12-28
> **maphco said:**
> Any help? :(

Hi and I am assuming you have enable the restricted drivers under system, administration.
 You may try using the nvidia settings to change the resolution. This command ```
gksudo nvidia-settings
```

---

### Post by maphco on 2007-12-28
I tried that command in the terminal, but nothiing happened that I can see.

---

### Post by overdrank on 2007-12-28
> **maphco said:**
> I tried that command in the terminal, but nothiing happened that I can see.

Ok well first backup your xorg
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup in case things don't work
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Then you can try and reconfigure your xorg **if you have enabled the restricted drivers**
```
sudo dpkg-reconfigure xserver-xorg
``` and choose nvidia as the driver and then answer the rest of the questions. If you do not know the answer then leave as the default answer given. If the reconfigure does not work then you can restore the previous xorg with the previous command from recovery mode. Good luck!

---

### Post by maphco on 2007-12-28
Now I remember something.  When I first installed Ubuntu I got an error when I tried installing the restricted drivers.  This was the error:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'

When I tried using

gksudo nvidia-settings

it asked me for my password, I gave it, but nothing happened after that...

---

### Post by overdrank on 2007-12-28
> **maphco said:**
> Now I remember something.  When I first installed Ubuntu I got an error when I tried installing the restricted drivers.  This was the error:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/nvidia-glx-new_100.14.19+2.6.22.4-14.10_i386.deb)
  Could not resolve 'ca.archive.ubuntu.com'

When I tried using

gksudo nvidia-settings

it asked me for my password, I gave it, but nothing happened after that...

Ok try using synaptic manager under system, administration. And search for nvidia-glx-new and try to install there.
Edit you may want to check your repos also
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by maphco on 2007-12-28
While looking for Synaptic I saw the link to Restricted Drivers, I went there and stupidly found the thing to install the nvidia driver I needed :p.  I restarted and now have a lot of resolutions to choose from, but when I click on one and hit apply it doesn't configure my desktop with the new settings.  When I go back to take a look at what res it's at it's stuck on 800x600.  Any suggestions at this point, Overdrank?

---

### Post by overdrank on 2007-12-28
> **maphco said:**
> While looking for Synaptic I saw the link to Restricted Drivers, I went there and stupidly found the thing to install the nvidia driver I needed :p.  I restarted and now have a lot of resolutions to choose from, but when I click on one and hit apply it doesn't configure my desktop with the new settings.  When I go back to take a look at what res it's at it's stuck on 800x600.  Any suggestions at this point, Overdrank?

Ok check your xorg and make sure it is using the nvidia driver and what does the nvidia-settings command do now?

---

### Post by maphco on 2007-12-28
It appears to have changed quite a bit:


Section "Device"
	Identifier	"nVidia Corporation C51 [GeForce 6150 LE]"
	Boardname	"NVIDIA GeForce 6800 (generic)"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"HP vs17"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [GeForce 6150 LE]"
	Monitor		"HP vs17"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1792	1344
		Modes		"1280x1024@60"	"1280x960@75"	"1280x960@60"	"1400x1050@60"	"1280x1024@75"	"1400x1050@75"	"1152x864@75"	"1600x1200@65"	"1024x768@60"	"1600x1200@60"	"1024x768@70"	"1792x1344@60"	"1024x768@75"	"832x624@75"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

tell me if you need the whole file pasted.

---

### Post by overdrank on 2007-12-28
Ok well this is a first for me
Identifier "nVidia Corporation C51 [GeForce 6150 LE]"
Boardname "NVIDIA GeForce 6800 (generic)"
Busid "PCI:0:5:0"
Driver "nvidia"
Screen 0
Vendorname "NVIDIA"
I am running one system on a Geforce 6100 and I have never seen the system that conflicts like this. Check the command ```
lspci 
``` to verify what the model of the card is. Also are you able to change the resolution with the command ```
gksudo nvidia-settings
```

---

### Post by maphco on 2007-12-28
I can barely fit the nvidia-settings window on my monitor, but there's an error when I try to change the res in there:

Failed to set MetaMode (12) 'CRT-0: 1280x1024@75 @1280x1024 +0+0' (Mode 1280x1024, id: 61) on X screen 0

Would you like to remove this MetaMode?

---

### Post by overdrank on 2007-12-28
> **maphco said:**
> I can barely fit the nvidia-settings window on my monitor, but there's an error when I try to change the res in there:

Failed to set MetaMode (12) 'CRT-0: 1280x1024@75 @1280x1024 +0+0' (Mode 1280x1024, id: 61) on X screen 0

Would you like to remove this MetaMode?

Ok can you verify the make of the graphics card with the lspci command.

---

### Post by maphco on 2007-12-28
I couldn't understand what was being shown to me, but when I went to nvidia-settings I verified it there, It is a GeForce 6150 LE.

---

### Post by overdrank on 2007-12-28
> **maphco said:**
> I couldn't understand what was being shown to me, but when I went to nvidia-settings I verified it there, It is a GeForce 6150 LE.

Ok please post the output of the command lspci. You can copy and paste the output.

---

### Post by maphco on 2007-12-28
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce 6150 LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
03:08.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
03:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem

---

### Post by overdrank on 2007-12-28
Ok it is the geforce 6150 and I have no idea why it is listed as a 6800 in the xorg. So the only thing I can suggest is to use the commands to back up you xorg 
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup if it fails to load desktop from the command line
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Then I would try and reconfigure your xorg with the command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and hopefully this will help. Good luck!

---

### Post by aimran on 2007-12-28
@ Overdrank's last post:

Shouldn't it be:

<code> sudo cp /etc/X11/xorg.conf-backup* /etc/X11/xorg.conf</code>


*originally conf.backup

---

### Post by maphco on 2007-12-29
That did the trick Overdrank.  Thanks a lot!  This resolution is sooo much more enjoyable! :D:D:D

---

