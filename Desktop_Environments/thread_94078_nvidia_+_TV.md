---
title: "nvidia + TV"
date: 2005-11-23
forum: Desktop Environments
---

### Post by atrus325 on 2005-11-23
Hey all,

I have an issue, and I hope someone can point me in the right direction.

Since the days of Hoary, I've had my computer hooked up to our TV, so that my wife and I can watch DVDs, etc.  I have a nvidia Gforce 4 card, and I've always used the nvidia driver (from apt), and things have been peachy.  The TV (which is just a fairly new crt - not an LCD or anything fancy) has always flickered to a higher resolution (1024x768) once the nvidia splash popped up, and I was able to get a complete desktop.

But the other day I installed Breezy on my box, installed nvidia-glx (7667), and now rather than flickering to the nvidia splash, the box gives me a black screeen and x locks up.  It boots alright using the nv driver, but it doesn't change resolution, and I'm stuck looking at just the upper left corner of the screen.  The little "screen resolution" gui in gnome presents only the option to use 640x480:60.

I know the nvidia-glx stuff works fine; it boots into gnome, spash and all, using my monitor, but that's it.

So far, I've tried three driver install methods:
1) apt-get using Breezy repositories
2) apt-get using Hoary repositories
3) removed all Ubuntu nvidia stuff and installed the NVIDIA-installer*.run file from the nvidia website.

I guess that means this is a problem with my xorg.conf monitor settings, but I don't have any idea what to do with monitor stuff.

Or, does Breezy now have some other controls that superceed xorg.conf settings?

Anyway, here's the pertinent stuff from my xorg.conf:

-----------------------------
Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
-------------------------------
Section "Device"
        Identifier      "NVIDIA Corporation NV20DCC [Quadro DCC]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection
-------------------------------
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection
-------------------------------
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV20DCC [Quadro DCC]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640$        EndSubSection
-----------------------------------

Thanks all :-)

J.

---

### Post by atrus325 on 2005-11-23
Nevermind; I just reverted to Hoary, and it works again.

Sorry Breeze.

J.

---

