---
title: "[SOLVED] Requirements for desktop effects"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by G. Cotgreave on 2007-11-17
Hi people!!!!

Since i am still new in Ubuntu (i installed them 2 months ago) i haven't yet enable the desktop effects. I tryed to do it when i had the feisty fawn but crazy things happened actually i couldn't see anything just a white screen and after i tryed for the second time i got a message that the desktop effects couldn't be enabled!!! Since then i was afraid to do it again!!! But as i work more with ubuntu i started to be jealus of the cube effect and others!!! My computer is a laptop Intel P4 2.0 GHz with 512Ram Nvidia graphics card and my screen supports 1024x768 max resolution. Does anybody have any idea if the desktop effects will work on that machine now that i got 7,10 and how to ''safely'' enable them?

---

### Post by Zorael on 2007-11-17
I don't see why it shouldn't work on that machine.

Are you running the restricted Nvidia drivers? There should be a Restricted Drivers Manager or something to the such in your Administration menu.

---

### Post by G. Cotgreave on 2007-11-17
I am not sure about the restricted drivers and unfortunantly i am at work now and i don't have my laptop with me to check but if i assume that there is a restricted drivers manager in the administration menu what should i do with that or how is it going to help me? sorry but i am a completly noobie :(

---

### Post by psyopper on 2007-11-17
You are correct, I do believe the Restricted Drivers Manager is in System-Administration.

When you open it it will list all of the devices in your system that require "Restricted" (Non-Free or Non-OpenSource). Your Nvidia card will be listed. Check the box and click OK/Apply.

Good luck!

---

### Post by G. Cotgreave on 2007-11-17
Since i am still at work i will try that when i get home and tell you the results in a few hours. Thakn you very much people!!!!!!

---

### Post by G. Cotgreave on 2007-11-17
so! my nvidia card is not in the list of the restricted drivers. is that good or bad? how can i see witch model of nvidia is on my computer? should i download the drivers myself somehow? help!!!

---

### Post by carlos1992 on 2007-11-17
you should install the drivers there are tons of help for Nvidia (sum people say that Nvidia has better support on ubuntu that Window$)
[http://www.youtube.com/watch?v=HpcAbSviAwU](http://www.youtube.com/watch?v=HpcAbSviAwU)

and if you don't find the drivers is because you haven't enable universe and multisource (sinaptics)
if you need more help post more!!!

---

### Post by G. Cotgreave on 2007-11-17
ok i just checked the synaptic pacage manager and all the repositories are enabled and also the one that says restricted. should i add any other repisitory to get the drivers ?

---

### Post by G. Cotgreave on 2007-11-17
i just saw the video link and on the add remove program list i have enabled the restricted drivers manager but when i type nvidia i can't see the nvidia drivers pacages the guy on the video shows

---

### Post by Forlong on 2007-11-18
Alright, let's get us some infos:

Post the output of
```
lsb_release -a
```
and
```
lspci | grep VGA
```
and
```
grep -v ^# /etc/X11/xorg.conf
```
and use the forum's CODE tag please (# button)

---

### Post by G. Cotgreave on 2007-11-18
lsb_release -a
```
george@george-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

```

lspci | grep VGA
```
george@george-laptop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

grep -v ^# /etc/X11/xorg.conf
```
george@george-laptop:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
        Driver          "sis"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

So here are the outputs that you asked. I don't understand sh** so i am compeletely on your hands!!!!!

---

### Post by psyopper on 2007-11-18
I think I see the problem...

The command lspci means List (ls) PCI Devices (pci), grep means "look for" and the VGA is what tyou are "grep"-ing.  So when we listed our VGA devices we came up with:

"Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP"

This is not an Nvidia video card. This is likely an on-board (on your motherboard) video card. the SiS cards generally do not support any sort of 3D rendering which is required for Compiz to work properly. 

One of two things is happening here - either you do not actually have an Nvidia video card installed, or if you do have one installed, your computer is not using it. 

Do you know for sure that you have an Nvidia video card installed?

---

### Post by G. Cotgreave on 2007-11-18
No i cannot be sure about the nvidia card i think i saw nvidia written when my computer starts but i am not sure :( is there anything i can do to get the effects working?

---

### Post by Forlong on 2007-11-18
> **G. Cotgreave said:**
> So here are the outputs that you asked. I don't understand sh** so i am compeletely on your hands!!!!!
OK, sorry... let me shed some light:
the first one tells us, what version of Ubuntu you are using
the second one shows the graphics card/cip in use
and the last one is your xorg.conf where I can see what driver you are using.

The question is... do you have a Nvidia card *besides* the SiS chip in your computer? Because you can't run Compiz in that one.

---

### Post by G. Cotgreave on 2007-11-18
i am afraid that not :( so i am doomed right? :(

---

### Post by Forlong on 2007-11-18
I'm afraid that's the case (in terms of desktop effects).

If it's not a notebook, go get a Nividia card. :)

---

### Post by G. Cotgreave on 2007-11-18
it is a notebook:( so i will just forget about them but thnx for the help people!!!!! The comunity is wonderfull!!!!

---

### Post by SoDanishWasLike on 2008-01-05
What are the system requirements for desktop effects?

Is a Pentium M 1.7GHz, 1 GB of RAM and a 32 MB ATI Radeon enough?

---

### Post by Forlong on 2008-01-06
I think so. What kind of Radeon, though?

---

### Post by SoDanishWasLike on 2008-01-06
> **Forlong said:**
> I think so. What kind of Radeon, though?

Mobility Radeon 9200 32MB

---

### Post by Forlong on 2008-01-06
The card is a little low-key but the effects should be working out of the box - have you already tried?

---

### Post by Fir3chi3f on 2008-01-06
I would not suggest ati especially for a new user.

Nvidia is usually easy to get working in ubuntu

---

