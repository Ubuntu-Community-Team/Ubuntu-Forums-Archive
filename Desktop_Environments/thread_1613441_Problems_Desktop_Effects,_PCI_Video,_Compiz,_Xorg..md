---
title: "Problems: Desktop Effects, PCI Video, Compiz, Xorg. Enough is Enough!!!!!"
date: 2010-11-04
forum: Desktop Environments
---

### Post by capsitan on 2010-11-04
[SIZE=3]Summary: I would like to enable desktop effects on my computer. I tried to do a compiz-check to see if compiz would run. Compiz then gave me the following:
[SIZE=4]
[/SIZE]```
 More than one graphics chip detected -- sorry, the script can not handle that. Aborting.
```[/SIZE][SIZE=3]

I have two video cards:  onboard and PCI. I figured that if compiz was saying that more than one chip was detected than I should simply change the priority in the BIOS from VGA/PCI to PCI/VGA. Here is where it gets weird.** Whenever I try to boot unbuntu or Linux Mint or any other distro using the PCI as first priority I either get to this Initramfs> boot screen or freeze on splash screen**. WTF!! I actually have to pick VGA as the first priority in order to get my PCI Radeon 7000 card to work. I am honestly stuck at this point. I need to enable compiz but i thinks its using two adapters. can i change my Xorg.conf file? here is lspci output:
[/SIZE]
```
[SIZE=3]
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
03:0a.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
03:0b.0 Ethernet controller: Atheros Communications Inc. AR5007G Wireless Network Adapter (rev 01)
03:0d.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
03:0f.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
03:0f.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
[/SIZE]
```[SIZE=3]
[/SIZE]

---

### Post by Joe of loath on 2010-11-04
Have you disabled the onboard chip in the BIOS?

Also, don't expect compiz to run on a Radeon 7000. They're 10 year old tech.

---

### Post by 3Miro on 2010-11-04
Boot priority is different then disabling a video card altogether. There should be another option in your BIOS somewhere.

Also, your hardware cannot handle the OpenGL effects from Compiz.

---

### Post by capsitan on 2010-11-05
[SIZE=3]
Thank you for both replying[/SIZE]. [SIZE=3]I actually cannot completely disable onboard graphics from my BIOS; I know it like the back of my hand as well. I ended up actually just removing the old PCI card and going with the onboard graphics. I think it would actually work better than the PCI card would anyway. I can actually run compiz-check now and here are the results:

[/SIZE][SIZE=3]Gathering information about your system...

[/SIZE]```
 Distribution:          Linux Mint 9
http://www.linuxmint.com/rel_isadora.php
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```[SIZE=3]

what do I do from here? I am still pretty new to Linux and have been very excited to learn more about it. All i have wanted to do was enable 3d and desktop effects the entire time, which then led me so far to a week trying to figure this out. 

What I am very confused about is why the filesystem wont mount when i change the priority to from VGA/PCI to PCI/VGA.  I found a couple of other threads online where this has been due to an issue with Linux and PCI cards. I am somewhat knowledgeable about computers (A+ and degree) and I still have no idea why this would happen. Maybe ill go for a Linux+ ;-)
[/SIZE]

---

### Post by 3Miro on 2010-11-05
>  Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

I am sorry to tell you that the 3D cube requires OpenGL rendering on a newer Intel, ATI or Nvidia (older Nvidia may work, however, older ATI cards have very bad driver support and should be avoided for Linux).

[http://en.wikipedia.org/wiki/Compiz](http://en.wikipedia.org/wiki/Compiz)

Basically, to get the Cube, you will have to get newer hardware.

---

### Post by capsitan on 2010-11-07
Um ok Well i have an intel integrated Video card that has 3D capabilities (see above). is there a way to manually invoke rendering?

---

### Post by capsitan on 2010-11-07
I looked around and it seems that I need to add a section called "server layout" to my Xorg file. here is my current Xorg:

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri2"
    Load  "FGL.renamed.libglx"
    Load  "dbe"
    Load  "glx"
    Load  "record"
    Load  "dri"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"
    Option      "Accelmethod" "XAA"                        
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        Option     "PageFlip" "true"              # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by capsitan on 2010-11-10
bump.

Anyone help me?

---

