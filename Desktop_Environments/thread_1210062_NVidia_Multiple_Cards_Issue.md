---
title: "NVidia Multiple Cards Issue"
date: 2009-07-11
forum: Desktop Environments
---

### Post by bkrausz on 2009-07-11
Hello,

I'm having an issue with getting a second video card working.  Here's my setup:

My lspci output:
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)
05:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

The G84 is in my PCIe slot, hooked up to my main desktop monitor & my TV (both DVI).  The NV17 is hooked up to my secondary monitor.

The secondary monitor doesn't load with the following error in Xorg.0.log:
(WW) NVIDIA(0): The NVIDIA GeForce4 MX 440 GPU installed in this system is
(WW) NVIDIA(0):     supported through the NVIDIA 96.43.xx Legacy drivers.
(WW) NVIDIA(0):     Please visit [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html) for
(WW) NVIDIA(0):     more information.  The 180.44 NVIDIA driver will ignore
(WW) NVIDIA(0):     this GPU.  Continuing probe...

My G84 is too new to be supported by the older drivers (or so it seems...I think X crashes massively when I use it, based on the one line in my logfile: "Backtrace"), plus I doubt it would work too well, being so old.

Long story short, I'm fairly confident that the legacy driver won't work.  Is there some other driver I can use, or some other way to get that 2nd card working?

Not that it's anything special, but below is my xorg.conf.  Ideally I'll run something like xmove or Xinerama over different video cards, but I figured I should probably just get them working first.

Thanks,
Brian

===============
> 
Section "Device"
        Identifier      "nvidia0"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen 0
EndSection

Section "Device"
        Identifier      "nvidia1"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen 1
EndSection

Section "Device"
        Identifier      "PCI"
        Driver          "nvidia"
        BusID           "PCI:5:0:0"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
EndSection

Section "Monitor"
        Identifier      "Monitor1"
EndSection

Section "Monitor"
        Identifier      "Monitor2"
EndSection

Section "Screen"
    Identifier  "Screen0"
    Device      "nvidia0"
    Monitor     "Monitor0"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1680x1050" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen1"
    Device      "nvidia1"
    Monitor     "Monitor1"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1920x1080" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "Screen"
        Identifier      "Screen2"
        Device          "PCI"
        Monitor         "Monitor2"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "ServerLayout"
        Identifier      "Server"
        Screen  0 "Screen0"
        Screen  1 "Screen1" rightOf "Screen0"
        Screen  2 "Screen2" leftOf "Screen1"
EndSection

---

### Post by Dave_Connor on 2009-07-11
Have you checked your BIOs settings to see if anything may be causing conflicts ?

---

### Post by bkrausz on 2009-07-12
BIOS settings seem to be fine...I can specify which one to primarily boot from, and that one is the only one that works (if it's the PCI card it boots into the limited-graphics-oops-stuff-went-wrong mode).

---

### Post by dotman on 2009-07-15
I am having the same exact problem as you, bkrausz. I am using:

01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
03:02.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)

And getting the same error. 

My 9800 works with the 173 driver so I was thinking about getting a FX5200 which uses the 173 driver too, to see if that is the extent of the issue. 

Or maybe there is a way to download the 96 driver and make a custom module to load into the kernel like "nvida_old".

I am trying to get TwinView to load on the 9800 and another X display on the 4000. I'll let you know if I find anything out.

---

### Post by dotman on 2009-07-17
I bought an 8400GS and it worked instantly. Except now I am having trouble launching apps in the second X session (when Xinerama is turned off). That is a different problem though :P

---

