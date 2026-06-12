---
title: "won't boot to gnome anymore"
date: 2009-06-07
forum: General Help
---

### Post by MrLobster on 2009-06-07
I'm unable to boot into gnome.  I've tried failsafe and get to the command prompt and have tried the last menu option to fix graphic problems but it didn't help.  The machine starts to boot and then freezes in a graphically glitched way.  Screen shows two fuzzy images of the Ubuntu boot screen at the top and the bottom is all glitchy.  

I'm guessing this happened because I installed proprietary ati drivers and the last time I was booted into gnome to try and fix a minor 3D glitch I was experiencing.  

I tried copying the xorg.conf.failsafe over the xorg.conf file but the problem remains and I have no idea how to fix it.  Can someone help?

---

### Post by merlinus on 2009-06-07
At the CLI try this:

sudo dpkg-reconfigure xserver-xorg

---

### Post by MrLobster on 2009-06-07
> At the CLI try this:

sudo dpkg-reconfigure xserver-xorg 

I tried this but it didn't fix it.

---

### Post by Locutus_of_Borg on 2009-06-07
from terminal
sudo nano /etc/X11/xorg.conf

locate where it says "Section "Device""

change the driver from whatever ATI driver you have listed, to vesa

save and exit

now you can at least use X/GNOME while you look for the correct driver for whatever card you have

---

### Post by MrLobster on 2009-06-07
It still not working :-?.  Maybe it isn't a problem with the video driver?  Here is my xorg.conf file (the same as xorg.conf.failsafe):
> 
Section "Device"
 	Identifier	"Configured Video Device"
 	Driver		"vesa"
EndSection

Section "Monitor"
 	Identifier	"Configured Monitor"
EndSection

Section "Screen"
 	Identifier	"Default Screen"
 	Monitor		"Configured Monitor"
 	Device		"Configured Video Device"
EndSection


---

### Post by Locutus_of_Borg on 2009-06-07
I dont know

does startx give any errors?
are there any errors in /var/log/Xorg.0.log?

---

### Post by MrLobster on 2009-06-07
startx causes the screen to be glitched up similar to normal booting.

The xorg.0.log file is apparently too big to be attached here (46.9 KB).  I don't know what to make of it.  Near the end it does say:
> 
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.


Here are the last several lines of the file:
> 
...
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 2.0
(II) VESA(0): VESA VBE Total Mem: 131072 kB
(II) VESA(0): VESA VBE OEM: ATI RADEON 9600 PRO
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) VESA(0): VESA VBE OEM Product: V350
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(II) VESA(0): virtual address = 0xaf648000,
	physical address = 0xe0000000, size = 134217728
(II) VESA(0): VBESetVBEMode failed...Tried again without customized values.
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE


The top several lines are:
> 

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux heron 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun  7 16:13:00 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 2

(--) PCI:*(0@1:0:0) ATI Technologies Inc RV350 AP [Radeon 9600] rev 0, Mem @ 0xe0000000/268435456, 0xfe9e0000/65536, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
...


---

### Post by Locutus_of_Borg on 2009-06-07
do```
grep EE /var/log/Xorg.0.log
```to print out just the errors

---

### Post by MrLobster on 2009-06-07
Looks like there are no errors in the log file. grep EE just gives: 
> 
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

---

