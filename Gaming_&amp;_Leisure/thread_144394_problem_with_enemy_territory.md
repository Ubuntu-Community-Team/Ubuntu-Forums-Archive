---
title: "problem with enemy territory"
date: 2006-03-14
forum: Gaming &amp; Leisure
---

### Post by fizz on 2006-03-14
I just installed ET with no problems. When i start the game, the sound, and video appear to be ok, although i cant get it to go full screen. The problem im having though is in the game, the mouse will barely move, its very unresponsive making it a pain just to go into menu's.

My gnome is setup with compiz/xgl, however ive tried with and without it enabled and makes no diffrences.

My machine is more the powerfull enough to handle this game, its a athlon 64 3200, 1 gig ram, and a geforce 6800. im running dapper x86 version.

---

### Post by BradChandler on 2006-03-14
Have you installed the nvidia drivers? Here's a thread that explains how in case you haven't:

[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers)

---

### Post by fizz on 2006-03-14
Ya, ive got the latest drivers installed, it was a pre-rec for xgl/compiz..

heres the relevent section of my xorg.conf..


```

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
#       Load    "dbe"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6800]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
        VideoRam        128000
        Option          "NvAGP"                 "3"
EndSection

Section "Monitor"
        Identifier      "DELL 2005FPW"
        Option          "DPMS"
        HorizSync       31-83
        VertRefresh     56-75
        Modeline        "1680x1050@60" 154.20 1680 1712 2296 2328 1050 1071 1081 1103
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV40 [GeForce 6800]"
        Monitor         "DELL 2005FPW"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

```

I didnt post the whole thing, but if you need me to, I can..

Also, if this helps...

```

kelly@gitrdun:~$ dpkg --list | grep nvidia
ii  nvidia-glx                             1.0.8178+2.6.15.7-1                  NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-kernel-common                   20051028+1                           NVIDIA binary kernel module common files
kelly@gitrdun:~$ 

```

---

### Post by fizz on 2006-03-15
Ok, I installed ET recently and went to play, however the sound and video play fine, but my mouse is like its on qualudes or something. It just doesnt move much, i have to struggle to get it to do much. For example, if i move the mouse way right, im lucky if the cursor moves like an inch, and its spotty at best when doing that as well. It works fine in gnome, but havent tested on any other games yet, im still getting my new box setup and looking for some help..

My glxgears score is 13000 average

im using compiz/xgl as well
here is the relevant sections of my xorg.conf

Something i just noticed, its probably my mouse drivers for xorg, im using a logitech mx800 cordless mouse/keyboard combo.. 

```

#OLD MOUSE CONFIG
#Section "InputDevice"
 #       Identifier      "Configured Mouse"
  #      Driver          "mouse"
   #     Option          "CorePointer"
    #    Option          "Device"                "/dev/input/mice"
    #    Option          "Protocol"              "ExplorerPS/2"
   #     Option          "Emulate3Buttons"       "true"
#EndSection 

#NEW MOUSE CONFIG
Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB Receiver"
    Option        "Dev Phys"        "usb-0000:00:02.1-2/input1"
        Option        "Device"        "/dev/input/event1"
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection

```
*Note: followed the logitech mx* guide, havent tested yet though..


Its not mouse sensitivity either, I just dont know how to explain the jittery, sluggishness of the mouse..

---

