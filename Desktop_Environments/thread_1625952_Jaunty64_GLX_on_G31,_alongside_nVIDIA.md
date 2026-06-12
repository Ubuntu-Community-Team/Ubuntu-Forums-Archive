---
title: "Jaunty64: GLX on G31, alongside nVIDIA"
date: 2010-11-19
forum: Desktop Environments
---

### Post by Ken_g6 on 2010-11-19
First a little background.  I've been using this system for over a year with the built-in Intel G31 chipset graphics.  Then I decided to get an nVIDIA card to run Folding@home, among other things.  I found that I had to run the graphics off the nVIDIA card to get Folding to run, but that caused jerkiness.  So then I discovered [these instructions]("http://foldingforum.org/viewtopic.php?f=52&t=6793") (which are one of several reasons I don't want to upgrade from Jaunty at this time.)  I'm now using my Intel card for the display, and my nVIDIA card for Folding.

The only problem with this setup is that I can't enable Compiz, or do other graphically-intensive stuff like certain games.  For now I'm using Metacity. Running glxinfo provides me with the following nice message:

```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault
```Yes, it segfaults at the end!  To clarify, here are my two GPUs:
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation Device 0e22 (rev a1)

```Based on other threads, and the fact that Compiz worked before I installed the new card, I assume that uninstalling the nVIDIA drivers is one option.  But that would defeat the purpose of the whole setup.  So is there any way to get GLX, and hopefully Compiz, working on the G31, while keeping the nVIDIA card in there?

Thanks!

---

### Post by Ken_g6 on 2010-11-20
Further information:

compiz-check won't run on my machine as-is: it says it's not designed for two graphics cards at once. When I modified it to look at only the Intel card (with several head -1's), I got the following:
```

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)
```I also tried this /etc/X11/xorg.conf file, to no effect. (No positive effect, but no negative effect either!):
```
Section "Device"
    Identifier    "Configured Video Device"
    Boardname "intel"
    Busid "PCI:0:2:0"
    Driver "intel"
    Screen 0
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "Module"
    Load "glx"
    Load "GLcore"
    Load "v4l"
EndSection
```

I really don't know what I'm doing there, so it's possible this is just failing and defaulting to some standard settings.  The previous file I had was very standard:```


Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```
How do I determine the Busid of my card?

---

### Post by Ken_g6 on 2010-11-21
Alright, I think I've figured out the problem, and I'm close to a solution.  It looks like, when I installed the nVIDIA drivers, it replaced /usr/lib/xorg/modules/extensions/libglx.so with a soft-link to its own nVIDIA libglx.so.260.19.14.  I tried removing the soft-link, but that just caused different errors in my Xorg.0.log.

So I checked a few other copies of Ubuntu I have lying around.  One is a 32-bit Jaunty in a VM (on the same machine.)  It has a libglx.so, but the sizes of the other files differ from my 64-bit installation, so I assume all those files are 32-bit specific.  

So, where/how can I easily get a copy of the original libglx.so?  I expected I could reinstall something in Synaptic, but so far I haven't found the right thing.  I guess if I get no answers in the next few days I could try installing Jaunty 64 to a new VM to get the file, but surely there's an easier way?

---

### Post by Ken_g6 on 2010-12-08
Yes!  It worked!  I finally got the file from the installation CD image, by extracting the filesystem.squashfs and loopback mounting it.  And I'm now running Compiz! :)

Edit: I should also mention that [these instructions](https://lists.launchpad.net/sony-vaio-z-series/pdfThd1noX7x2.pdf) (PDF) helped get a few other files in place.

Thanks for...um, listening? :-\"

---

