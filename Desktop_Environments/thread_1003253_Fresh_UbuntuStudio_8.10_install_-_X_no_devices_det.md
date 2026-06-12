---
title: "Fresh UbuntuStudio 8.10 install - X: no devices detected"
date: 2008-12-05
forum: Desktop Environments
---

### Post by CactusCoder on 2008-12-05
I acquired a Gateway DX4200-UB001A Refurbished Desktop PC - AMD Phenom X4 9550 Quad Core, 6GB DDR2-667.

After installing UbuntuStudio 8.10 the X server won't start - (EE) No devices detected.

It appears that the motherboard includes an ATI Radeon HD 3200 video adapter, but its ports are taped over saying not to use them. My guess is that the adapter died and the customer returned the PC and Gateway fixed the problem by adding an ATI Mobility Radeon HD 3450 video adapter.

Problem appears to be that the Xorg dynamic video hardware recognition is getting confused by the two video adapters. The detailed log reported the two ATI adapters: 
PCI: (0@1:5:0) ATI Radeon HD 3200 Graphics rev 0
PCI: (0@2:0:0) ATI Mobility Radeon HD 3450 rev 0

I downloaded the latest ATI Radeon driver package from ATI, but I cannot build it - it seems my system isn't ready yet to do compiles...

I would like to get at least X started using the video driver that is used during the boot process - or something. I'm not very good with the command-line interface :-(

So my question is - what do I need to do to get my system to boot into Gnome.

My monitor is an I-Inc TW191D.

PS. The PC came with Windows Vista Home Premium installed. I booted into Vista a few times to make sure all the hardware was working before I replaced Vista with UbuntuStudio.
PPS. I could not find a way to disable the HD 3200 from the BIOS settings.

---

### Post by CactusCoder on 2008-12-06
Installed the RADEONHD driver via apt-get and located a sample xorg.conf file for the Radeon.

X now recognizes the adapter but pukes on trying to copy the BIOS. Had a closer look at what was being reported in the log and noticed it listed a bunch of question marks for the BIOS address - seems to jive with the inability to read the BIOS...

So perhaps I have the HD 3200 and HD 3450 backwards - I switched the device to the HD 3200 but that made it not recognize the adapter. 

Suggestions anyone?

My xorg.conf:
```
Section "Device"
        Identifier      "ATI Technologies Inc ATI Default Card"
        Driver          "radeonhd"
        BusID           "PCI:2:0:0"
        Option "XAANoOffscreenPixmaps" "true"
        Option "AllowGLXWithComposite" "true"
        Option "RenderAccel" "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       24-80
        VertRefresh     49-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc ATI Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1440x900"
        EndSubSection
        Option "XAANoOffscreenPixmaps"
        Option "AddARGBGLXVisuals" "true"
EndSection



Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
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
```

---

### Post by CactusCoder on 2008-12-06
This appears to be a bug in X server: [https://bugs.launchpad.net/opensuse/+source/xorg-server/+bug/267241/+activity]("https://bugs.launchpad.net/opensuse/+source/xorg-server/+bug/267241/+activity")

From the bug report:
> You have 2 graphic cards and xorg doesn't know which one to choose as primary adapter. You need to define it in section "Device" of your xorg.conf config file with a line like: BusID "PCI:02:00:00" run lspci to find the right pciid.

lspci tells me the PCIID is 02:00:0 - changed my xorg.conf.

Now all I get is a blank screen - I press ENTER and the X Server log is displayed, so for some reason the initial failure screen is invisible to me.

(EE) RADEONHD(0): Cannot read BIOS image - followed by an empty backtrace...

From detailed log:
> (II) RADEONHD: version 1.2.1, built from dist of git branch master, commit 761940fd
(II) Primary Device is:
<lists a bunch of resource ranges>
(II) Setting vga for screen 0.
(**) RADEONHD(0): Depth 24, (--) framebuffer bpp 32
(**) RADEONHD(0): Selected ShadowFB.
(II) RADEONGD(0): Unknown card detected: 0x95C5:0x1462:0x1390.
  If - and only if - your card does not work or does not work optimally
  please contact radeonhd (at) opensuse.org to help rectify this.
  Use the subject: blah-blah-blah


So it looks like I'm stuck with a PC that can't run 8.10 for now :-(

---

