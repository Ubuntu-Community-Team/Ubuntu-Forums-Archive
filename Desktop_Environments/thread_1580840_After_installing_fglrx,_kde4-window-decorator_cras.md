---
title: "After installing fglrx, kde4-window-decorator crashes when I run compiz"
date: 2010-09-24
forum: Desktop Environments
---

### Post by soulspit on 2010-09-24
Hi everyone,

I was using the open source ATI drivers and KDE's compositing worked, so I hadn't installed compiz.  I wanted to try fglrx because I thought a) I might be able to get temperature readings, and b) it might stop Kubuntu from making my computer incredibly hot (in Windows 7 it stays cool).  So I installed fglrx by enabling it in the restricted hardware drivers thing, and things worked, but compositing was disabled and no matter what I did I couldn't enable it.  So I installed compiz.  When I run compiz, I get the following output:

```
toby@tensile:~$ compiz --replace
Starting kde4-window-decorator
kde-window-decorator(5950) KWD::KDecorationPlugins::loadPlugin: kwin : path  "/usr/lib/kde4/kwin3_oxygen.so"  for  "kwin3_oxygen"
KCrash: Application 'kde4-window-decorator' crashing...
sock_file=/home/toby/.kde/socket-tensile/kdeinit4__0
```and, as you can see, the window decorator crashes, so I have no window borders, which makes life difficult, even though everything else in compiz works and looks beautiful.

I've been researching this stuff for a while now but can't find anything that fixes it.  My crash is identical to [this bug]("https://bugs.kde.org/show_bug.cgi?id=232213"), but on the bug report it says it is already fixed in compiz, but this doesn't seem to be the case...  So, why might this be?  I'm running Kubuntu Lucid 64, on a Dell Studio 1747.  Here is a lot of info about my system:

```
toby@tensile:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4650
OpenGL version string: 3.2.9756 Compatibility Profile Context
``````
toby@tensile:~$ glxinfo | grep rendering
direct rendering: Yes
```the gears work:```
toby@tensile:~$ glxgears
39886 frames in 5.0 seconds
41384 frames in 5.0 seconds
toby@tensile:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
9976 frames in 5.0 seconds = 1995.200 FPS
11576 frames in 5.0 seconds = 2315.200 FPS
```my xorg.conf:```
Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection
```The only thing I have found that is at all productive is running [Forlong's compiz-check script]("http://forlong.blogage.de/entries/pages/Compiz-Check").  I get the following:

```
toby@tensile:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   KDE4
 Graphics chip:         ATI Technologies Inc M96 [Mobility Radeon HD 4650]
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```yet:
```
toby@tensile:~$ cat /var/log/Xorg.0.log | grep AIGLX
(II) AIGLX: Loaded and initialized /usr/lib64/dri/fglrx_dri.so
```I have no errors (EE) in the Xorg log, though some warnings:
```
toby@tensile:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) Falling back to old probe method for fglrx
(WW) fglrx: No matching Device section for instance (BusID PCI:0@2:0:1) found
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
```Sorry for the masses and masses of output, but I don't really know what's helpful and what's not.  Please, I would very much like compiz (or compositing - why is kwin's not working?) to work, so any help would be very much appreciated, and I think that a lot of people (judging by the masses of duplicate bug reports for this) are having this problem, so you'd be helping a lot of people out!

---

### Post by soulspit on 2010-09-25
Bump please!  I don't think I have a particularly unique configuration - others must have had this problem.  Care to lend a hand?

---

### Post by soulspit on 2010-09-27
A final bump, if I may.  Compiz, fgrlx, kde window decorator, problems, ring a bell, anyone?

---

### Post by soulspit on 2010-12-20
For the record, for any folks out there dealing with the same issue: after struggling for a while, I gave up and replaced my window decorator, replacing KWin with Emerald.  Emerald is a pretty good choice to begin with, and it plays nice with compiz.

---

