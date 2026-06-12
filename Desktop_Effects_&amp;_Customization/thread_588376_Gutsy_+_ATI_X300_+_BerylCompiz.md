---
title: "Gutsy + ATI X300 + Beryl/Compiz"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by tadah on 2007-10-23
Hey there fellow ubunters [IMG]http://static.linkomanija.net/pic/smilies/wave.gif[/IMG]

I just can't get it right and can't find the solution anywhere [IMG]http://static.linkomanija.net/pic/smilies/wall.gif[/IMG]
Could anyone help me with this? Maybe a HOWTO or sth [IMG]http://static.linkomanija.net/pic/smilies/rolleyes.gif[/IMG]
[IMG]http://static.linkomanija.net/pic/smilies/please.gif[/IMG]

Thanks in advance! [IMG]http://static.linkomanija.net/pic/smilies/wink.gif[/IMG]

---

### Post by digifan on 2007-10-23
Did you upgrade or did you make a fresh install?
It could matter as it did with me.

I upgraded and some remnants off compiz configfiles and programs remained. I don' t know why but it did. BTW I have ATI X700 mobilty (RV410).

Here' s what I did:
I removed all connected to compiz and beryl (commands won' t hurt if it allready uninstalled.
Frome a terminal run:
"sudo apt-get remove beryl" en  "sudo apt-get remove compiz"
then install the restricted drivers module (seems to work better for me i.s.o. the open source driver)
"sudo apt-get install linux-restricted-modules-2.6.22-14-generic" and install compiz-fusion after this "sudo apt-get install compiz" and " sudo apt-get install ccsm".
Now after this go to the system management menu and select restricted driver option.
mark the ATI driver and close. This will install the fgrlx driver.
then restart X by ctrl+alt+backspace.
now compiz should be working. 
If not, check if following is in your Xorg.conf file (/etc/X11/Xorg.conf) look if texts in bold exists and change accordingly.

Section "Module"
    Load        "bitmap"
    Load        "ddc"
**    Load        "dri"**
    Load        "extmod"
    Load        "freetype"
**    Load        "glx"**
    Load        "int10"
    Load        "type1"
**    Load        "vbe"**
**    Load        "dbe"**
EndSection

Section "Device"
    Identifier    "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
    Driver        "fglrx"
    Busid        "PCI:1:0:0"
    Option        "MonitorLayout"    "LVDS,AUTO"
    Option        "XAANoOffscreenPixmaps"
    Option        "AGPMode"    "8"
    Option        "AGPFastWrite"    "true"
**    Option        "AddARGBGLXVisuals"    "true"**
    Option        "DisableGLXRootClipping" "true"
**#**       Option        "AllowGLXWithComposite" "true"
    Option        "EnablePageFlip" "true"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Extensions"
**    # **   Option        "Composite" "Enable"
**    Option        "Composite"    "0"**
EndSection

---

### Post by steve.dhondt on 2007-10-23
Hi
Thanks for your suggestions, I'm having the same problem
I had compiz working fine before, but upgrading to 7.10 messed it up. I did the reinstall as you suggested, when I checked the Xorg.conf file I found following lines you mensioned not there:

** Load "dbe"**
and:
** Option "AddARGBGLXVisuals" "true"**

I added them, but still no compiz.

---

### Post by tadah on 2007-10-23
I upgrated from 7.04 (fiesty).

Well I tried your guide, but it didn't work. The screen went white and i had to restore the xorg.conf. Maybe it's cuz i have x300, not x700.
Any more ideas how to solve this? [IMG]http://static.linkomanija.net/pic/smilies/detective.gif[/IMG]

damn is it like not possible for me to fix it? seems like nothing helps, always sth goes wrong [IMG]http://static.linkomanija.net/pic/smilies/confused.gif[/IMG]

of course, i'm also kinda noob with linux, however i'm trying [IMG]http://static.linkomanija.net/pic/smilies/dumbells.gif[/IMG] [IMG]http://static.linkomanija.net/pic/smilies/wink.gif[/IMG]

---

### Post by digifan on 2007-10-23
> **steve.dhondt said:**
> Hi
Thanks for your suggestions, I'm having the same problem
I had compiz working fine before, but upgrading to 7.10 messed it up. I did the reinstall as you suggested, when I checked the Xorg.conf file I found following lines you mensioned not there:

** Load "dbe"**
and:
** Option "AddARGBGLXVisuals" "true"**

I added them, but still no compiz.

Could you post your Xorg.conf file and the result of command lspci in a terminal?
I could have a look.

---

### Post by tadah on 2007-10-24
I know this was not for me, however I hope you could help me too. here are mine:

xorg.conf:
```

Section "Files"
EndSection

Section "Module"
	Load		"dri"
	Load		"v4l"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ATI Radeon (fglrx)"
	Busid		"PCI:1:0:1"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

and *lspci*
```

00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
06:02.0 Communication controller: Conexant HCF V90 56k Data/Fax/Voice/Spkp PCI Modem (rev 89)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 01)

```

---

### Post by steve.dhondt on 2007-10-24
```
~ $: lspci
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
02:09.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

and the xorg.conf:
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "dri"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
        Load            "dbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "be"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV350 AS [Radeon 9550]"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
        Option          "AddARGBGLXVisuals" "true"
EndSection

Section "Monitor"
        Identifier      "Bigtide-C770"
        Option          "DPMS"
        Horizsync       28-51
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 AS [Radeon 9550]"
        Monitor         "Bigtide-C770"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"      "640x400"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"      "640x400"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"      "640x400"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"      "640x400"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"      "640x400"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1024x768"      "800x600"       "640x480"      "640x400"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection
```

spotting anything fishy?
Like I said, I added the  **Load "dbe"**; and the  **Option "AddARGBGLXVisuals" "true"** after your instructions, they weren't there originally.

Oh, I don't know if this is a clue, but when I try to get desktopeffects trough system->preferences->apearences; I get a message saying: "the composite extension is not available". I checked and libxcomposite1 (if that *is* what they're talking about) should be installed according to synaptic package manager.

On another thread here I heard someone got it working after installing xserver-xgl
But that didn't do the trick for me either.

---

### Post by BolitoVT on 2007-10-24
I'm having the exact same problem with my Dell E510... I'm missing my Feisty Fawn & Beryl already :(

---

### Post by pay on 2007-11-06
The fglrx driver that is in the repositories isn't capable of AIGLX, only the lastest 8.42 fglrx driver and the open source dri ati driver is capable of aiglx.

---

### Post by adiladawi on 2007-12-17
dears

i was able to enabe compiz effects on my x300 ati card but by using the open source driver 

go to system > administration > screen and graphics

on graphic card tab window you will choose form the list of avaliable drivers

i choosed the second radio button (choose driver by name)

i selected ati mach8,mach16,mach32,... etc

down you will see avaliable drivers pick up ( opensource driver)

in the attachment a screenshot of my benchmark

the benchmark result without any open window reaches 90 FPS

---

### Post by aerorahul on 2007-12-18
can anyone post a howto for this.
The post has become a lot confusing.
thanks,
Dell E510 ATI Radeon X300

---

### Post by froghunter on 2007-12-18
Did you try going through and uninstalling the old driver and getting one of the new ATI ones? [This method]("http://ubuntero.org/cochise/weblog/718.html") didn't work for me because I restarted mid-way through after reading some others. I am a total noob, but I think I am going to check out the [newly released ATI driver]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-7-11-x86.x86_64.run") which should work. Hope it works for you, haven't gotten there yet.

---

### Post by strikoo on 2007-12-19
I have x300 integrated in x1150 chipset on my msi notebook.
Installed new ati drivers with envy, and everything worked nicely.
I also found this web site that was very helpfull.
[www.ubuntu1501.com](www.ubuntu1501.com)

cheers m8s

---

### Post by adiladawi on 2007-12-31
thanks after seeing your link and following the steps there my benchmark now reach 125 FPS

THANKS DUDE!!

---

### Post by aerorahul on 2008-01-14
I followed the suggested website by froghunter and went through the entire process with no errors. After reboot and Alt+F2 and then compiz, nothing happened. I went to Menu--Preferences--Appearence and then Visual Effects tab to enable the the effects at the custom button, but after a lot of thinking (5 secs) it said "Desktop effects could not be enabled". Earlier, before following thwebsite it used to say "Composite extention not found". So this is certainly progress but no where near success. 

Any pointers please?? It is boring to use without compiz. 

Thanks,
Rahul M.

---

