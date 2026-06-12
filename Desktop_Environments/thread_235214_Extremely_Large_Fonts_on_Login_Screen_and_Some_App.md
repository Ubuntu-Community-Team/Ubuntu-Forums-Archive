---
title: "Extremely Large Fonts on Login Screen and Some Apps...Why???"
date: 2006-08-12
forum: Desktop Environments
---

### Post by mgolus on 2006-08-12
I have been playing around with linux for some time.  On my laptop I run a copy of Dapper, which has been upgraded from Breezy.  I have no problems here.  Last night I installed a fresh installation of Dapper on a desktop that I plan to use as a media center (MythTV).  For some reason on the login screen, the font in the textboxes is at least 100pt font.  it is huge.  Needless to say, all you can see inside the box is a small portion of each letter.  This also has been happening on many of the apps that I am running.  The font that it renders takes up nearly the entire screen.  It did this on both the live CD and once it was installed on the desktop.  I have searched for quite some time on how to resolve the issue and have not been able to find anyone with a similar issue.  Any help would be much appreciated.

---

### Post by maniacmusician on 2006-08-12
It is probably a driver issue. please post your xorg.conf.

also, what if you run the live cd in safe graphics mode? that's what I have to do to get it to display things correctly.

---

### Post by jimmygoon on 2006-08-12
It could also be a DPI problem...

---

### Post by mgolus on 2006-08-12
Ok, I have posted a screenshot of an example app, and my xorg.conf is as follows (The only modifications I have done is to set the display to run at 1280x720): 


```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R200 QL [Radeon 8500 LE]"
	Driver		"ati"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"LCD Multi-Me"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline "1280x720_60.00"  74.48  1280 1336 1472 1664 720 721 724 746
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R200 QL [Radeon 8500 LE]"
	Monitor		"LCD Multi-Me"
	DefaultDepth	24
         SubSection "Display"
                 Depth   24
                 Modes   "1280x720_60.00"
         EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by maniacmusician on 2006-08-12
I don't really know if it is a DPI problem as I have no experience with those

But there is something that i see that could possibly be causing this problem. You're using the default driver "ati" which ubuntu automatically assigns to ATI graphics cards. Try installing the one provided by ATI themselves. Most people report that it works a lot better. its called fglrx. Instructions here: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) 
Try that. Hope it fixes it for you.

---

### Post by Anduu on 2006-08-12
There is an option that can be set in the monitor section of your xorg.conf that could solve your problem...

"DisplaySize"

To calculate what numbers to use take the resolution of your monitor, multiply by 25.4, then divide by the desired DPI. For Example if you run at 1600x1280 and want 100dpi : 1600 x 25.4 / 100 = 406 and 1280 x 25.4 / 100 = 325

Now go to your Monitor section in xorg.conf and enter:
```
 DisplaySize 406 325
```

It should end up looking like this:
```
Section "Monitor"
	Identifier	"LCD Multi-Me"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline "1280x720_60.00"  74.48  1280 1336 1472 1664 720 721 724 746
	DisplaySize 406 325
	Option "DPMS" "true"
EndSection
```

---

### Post by superm1 on 2007-03-27
> **Anduu said:**
> There is an option that can be set in the monitor section of your xorg.conf that could solve your problem...

"DisplaySize"

To calculate what numbers to use take the resolution of your monitor, multiply by 25.4, then divide by the desired DPI. For Example if you run at 1600x1280 and want 100dpi : 1600 x 25.4 / 100 = 406 and 1280 x 25.4 / 100 = 325

Now go to your Monitor section in xorg.conf and enter:
```
 DisplaySize 406 325
```It should end up looking like this:
```
Section "Monitor"
    Identifier    "LCD Multi-Me"
    Option        "DPMS"
    HorizSync    28-64
    VertRefresh    43-60
    Modeline "1280x720_60.00"  74.48  1280 1336 1472 1664 720 721 724 746
    DisplaySize 406 325
    Option "DPMS" "true"
EndSection
```
Thanks! I've been wondering how to properly calculate DisplaySize.  I've always just winged it ;)

---

### Post by kiyolee on 2007-10-23
Unfortunately, that does not work for me.
I am using 7.10 on a low-end Compaq notebook.
Screen resolution 1280x800 and so added the line:
DisplaySize 339 212

According to another thread:
[http://ubuntuforums.org/showthread.php?p=3609621](http://ubuntuforums.org/showthread.php?p=3609621)

Reset the Visual Effects can help the problem and does help for me.
But the setting cannot be saved and the problem comes back after reboot.

---

### Post by mohansoundar on 2007-10-27
The displaySize setting helped me !!
Thanks for helping me out in saving another couple of sleepless nights \\:D/
My toolbar problem is solved, but the login page huge font size remains, yet to solve it ](*,)

---

### Post by nikhilsinha on 2007-11-03
I too had this problem on my Machine with a SIS Chipset.

go to URL Described by "kiyolee"
[http://ubuntuforums.org/showthread.php?p=3609621](http://ubuntuforums.org/showthread.php?p=3609621)

The Method described by "pashashome" i.e.
Editing the file...
sudo gedit /etc/gdm/gdm.conf
did the trick for me!

WORKS perfectly!:KS

---

### Post by TuxCrafter on 2007-11-06
> **nikhilsinha said:**
> I too had this problem on my Machine with a SIS Chipset.

go to URL Described by "kiyolee"
[http://ubuntuforums.org/showthread.php?p=3609621](http://ubuntuforums.org/showthread.php?p=3609621)

The Method described by "pashashome" i.e.
Editing the file...
sudo gedit /etc/gdm/gdm.conf
did the trick for me!

WORKS perfectly!:KS

For font problems you can also take a look at my xserver and xfce font script.

---

### Post by hwheeler43 on 2007-12-12
:) It is really nice to be able to find solutions so easily. You folks rock.  The fix sudo gedit /etc/gdm/gdm.conf  worked like a champ on my Toshiba laptop.

---

