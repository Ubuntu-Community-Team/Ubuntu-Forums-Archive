---
title: "help with kde4 and dual head ati hd 3650"
date: 2010-02-26
forum: Desktop Environments
---

### Post by aarons6 on 2010-02-26
after switching from and nvidia to an ati card i have been left with a huge headache.

ive worked out everything and so far i have dual monitor support, full composite and no lockups or crashing.. 

but i have one problem.. 

my video card has one DVI and one VGA connector.. 
in gnome and xfce4 everything is right, the login screen is on the left, the taskbar on the left, compiz turned on, full effects.. but in kde, its on the right.. 

there doesnt seem to be any way i can see to rearrange the desktop in kde4?
im attaching a pic on what i mean.. 
desktop one (with cord 0 0), is the left desktop in gnome and xfce and is the way the xorg.con has it assigned.. 

but in kde4 desktop 1 and desktop 2 need to be switched around.. 

any ideas?

---

### Post by aarons6 on 2010-02-26
here is my xorg.conf.. as far as i know this is 100% correct to use the "big desktop" mode.

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "DFP2"
    Option        "VendorName" "Viewsonic"
    Option        "ModelName" "VA1912wSERIES"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1440x900"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "CRT2"
    Option        "VendorName" "Princeton"
    Option        "ModelName" "VL 1916"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "60"
    Option        "Position" "1440 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "ATI Radeon HD 3600 Series"
    Driver      "fglrx"
        Option        "DesktopSetup" "horizontal"
        Option        "Monitor-DFP2" "DFP2"
    Option        "Monitor-CRT2" "CRT2"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "ATI Radeon HD 3600 Series"
    Monitor    "Monitor0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   2720 2720
        Depth     24
    EndSubSection
EndSection

---

### Post by aarons6 on 2010-02-26
one more thing to note, about half way of loading kde4 you can see the monitors switch.
it goes from the gdm login screen on the left, to the kde splash screen on the right.

---

### Post by keforex on 2010-02-26
I have two 30" monitors and I had this problem before too.

My xorg.conf is below and I noticed that one of the differences is that my "monitor" and "screen" entries are numbered, and yours are not.

It works for me, main window on the left, menus on the left, etc...

Check the Section Device too.


Section "Monitor"
	Identifier     "monitor1"
	VendorName     "Hewlett-Packard"
	ModelName      "HP LP3065 Wide LCD Monitor"
	HorizSync       98.0 - 100.0
	VertRefresh     59.0 - 60.0
	ModeLine       "768x576" 50.0 768 832 846 1000 576 590 595 630
	ModeLine       "768x576" 63.1 768 800 960 1024 576 578 590 616
EndSection

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "HP LP3065"
	HorizSync       49.3 - 98.5
	VertRefresh     60.0
EndSection

Section "Screen"
	Identifier     "screen1"
	Device         "device1"
	Monitor        "monitor1"
	DefaultDepth	24
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Videocard0"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option         "TwinView" "1"
	Option         "TwinViewXineramaInfoOrder" "DFP-0"
	Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +2560+0"
EndSection

Section "Device"
	Identifier     "device1"
	Driver         "nvidia"
	VendorName     "nVidia Corporation"
	BoardName      "NVIDIA GeForce FX to GeForce 8800"
	Option         "DPMS"
	Option         "TwinViewOrientation" "Clone"
	Option         "ModeValidation" "NoWidthAlignmentCheck, NoDFPNativeResolutionCheck"
	Option         "AddARGBGLXVisuals"
	Option         "ExactModeTimingsDVI"
	Option         "TwinView"
EndSection

Section "Device"
	Identifier     "Videocard0"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce 8800 GTX"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


I hope this helps!!

---

### Post by aarons6 on 2010-02-26
yours looks the same as mine but for nvidia cards..
basically you make one large screen (screen0 2720x2720), then you tell the 2 smaller screens to go inside it. (DFP2 1440x900 starting from 0 0 and CRT2 2048x1024 starting at 1440 0)

im just not finding why kde thinks they are switched around when its working fine in gnome.

for now i just switch the panels around but certain windows force themselves on monitor 2 when i want it on monitor 1.

---

### Post by keforex on 2010-02-26
Do you have these 3 lines in your screen section?

Option "TwinView" "1"
Option "TwinViewXineramaInfoOrder" "DFP-0"
Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +2560+0"


Adjust the sizes to fit your monitors and give it a try...

---

### Post by aarons6 on 2010-02-26
those settings are for nvidia cards, i have an ati.

---

### Post by keforex on 2010-02-27
I see. But aren't the twinview options for ati also?

---

### Post by aarons6 on 2010-02-28
still no fix.. it has to be a bug in the ati drivers or kde4 beta...
both gnome and xfce4 recognize the monitors are the way they are described in the xorg.conf
as a test i put it like this.
Section "Device"
    Identifier  "ATI Radeon HD 3600 Series"
    Driver      "fglrx"
        Option        "DesktopSetup" "horizontal"
Option        "Monitor-CRT2" "CRT2"
        Option        "Monitor-DFP2" "DFP2"
    BusID       "PCI:1:0:0"
EndSection

and gnome and xfce4 switched the monitors around.. 

temp solution was to use the vga connector on my higher res monitor and the dvi one on the lower one.. now everything is correct..

i dont understand why ATI made a HD video card with one vga and one dvi and put the vga one first.

as per the xorg.0.log it says
(II) fglrx(0): Connected Display1: CRT on secondary DAC [crt2]
(II) fglrx(0): Connected Display2: DFP on secondary TMDS [tmds2i]
these do not change no matter how you write the xorg.conf file.. mon0 mon1 mon2 
this is how KDE is seeing it.. its ignoring the xorg.conf so im guessing its bad drivers with no kde correction ability. 

now i have a question.. since i guess this video card has 2 DACs can i get a cable that splits the dvi into each monitor? or am i stuck with vga and dvi?

cause i dont understand this part.
(II) fglrx(0): Output DFP1 disconnected
(II) fglrx(0): Output DFP2 connected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Output CRT2 connected

says i can have 4 monitors on this video card?

---

### Post by aarons6 on 2010-02-28
i narrowed it down to kde4s multiple monitor config program.
in the ati control panel it showing that crt is monitor 2 and dvi is monitor 1.

some reason kde thinks otherwise.

---

### Post by aarons6 on 2010-03-06
ok so after a lot of searching i figured it out.. it was really easy actually.. for anyone who has an ati card that wont cooperate this is how to make it work.

first off, when you switch video cards, its necessary to reinstall the openGL layers from synaptic.
this was what was actually causing me a ton of problems.. 
nvidia put in some opengl drivers and made a symlink to libGLcore.. well i removed the drivers with the installer it just deleted them and didnt remake the link to the originals.. 
installing the ati drivers just checked the links, didnt make sure they were actually linked to anything.

so ls -l came up with a lot of red files.. 

second.. this is how you setup a dual monitor with ati drivers.. i ended up with the ubuntu ones.
first, delete the xorg.conf file that contained all your nvidia settings.. 
second, type **sudo aticonfig --initial**
then **[B]sudo aticonfig &#8211;dtop=horizontal &#8211;overlay-on=1**[/B]
then in the xorg.conf under screen put
**virtual x y** (x being the size of both monitors horizontal and y is the tallest one)
i put 3488 1024
then if your like me and want to use the dvi on the main screen type.
**sudo aticonfig --swap-monitor --effective=now**
this will make the dvi number 1 and the vga number 2.. 

so after reinstalling the opengl core libraries, the open ubuntu ati catalyst drivers and doing those 3 commands, i now have, a dual monitor desktop of 4928x1024. (not sure why its bigger but it works.)
plus i have full effects without using xinerama.

---

