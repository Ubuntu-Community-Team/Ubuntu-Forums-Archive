---
title: "I need help installing my radeon X1300 PRO graphics card!"
date: 2009-06-06
forum: General Help
---

### Post by xZachtmx on 2009-06-06
Ok i desperately need your help with this as i am new with linux (looks very cool so far) but when i tried installing my driver it didnt seem to work... when i clicked on the cataclyst control center it said:

[I]"There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following: 

No ATI driver is installed, or the ATI driver is not functioning properly. Please install the ATI river appropriate for your Ati  hardware, or configure using aticonfig"[/I] 

so yea... id like to know how to get my driver properly running...

---

### Post by whoop on 2009-06-06
how did you try to install the driver? which method did you use?

---

### Post by xZachtmx on 2009-06-06
dowloaded ati-driver-installer-9-3-x86.x86_64.run and then made it run in terminal... it downloaded a bunch of stuff and now the cataclyst control center is on my computer... but it isnt running

---

### Post by xZachtmx on 2009-06-06
this is what happened when i typed fglrxinfo in the terminal:

xzachtmx@Zach-desktop:~$ fglrxinfo
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual!

... maybe that helps?

---

### Post by Legace on 2009-06-06
If you are using Ubuntu Jaunty (9.04):
The FGLRX driver doesn't support cards prior to the 2000 series.
So, unfortunately, you can't use the FGRLX driver if you're using Jaunty.

---

### Post by xZachtmx on 2009-06-06
ok... well is there a different version of ubuntu then? and is it just as good?

---

### Post by Legace on 2009-06-06
> **xZachtmx said:**
> ok... well is there a different version of ubuntu then? and is it just as good?

You could use 8.04 of Ubuntu and the 9.3 version of FGLRX.
Otherwise, you'd have to stick to the open source radeon driver, which doesn't support 3D acceleration (yet).

---

### Post by xZachtmx on 2009-06-06
well when will it support 3d? and where can i get it?

---

### Post by neo.patrix on 2009-06-06
> **xZachtmx said:**
> well when will it support 3d? and where can i get it?

ahem ... who knows such things except the oracle.

You can check [here]("https://help.ubuntu.com/community/RadeonDriver")

Btw, since this on-going post on ATI cards, what is the difference between Radeon X1300 and Mobility Radeon X1300? Somehow I have never able to figure it out so far.

---

### Post by Yellow Pasque on 2009-06-06
The open-source radeon driver DOES support 3D for this card, as it's an R500 part. It's the "RadeonHD" (R600/R700) cards that don't have open-source 3D at the moment (it's under development).

---

### Post by Legace on 2009-06-06
> **Temüjin said:**
> The open-source radeon driver DOES support 3D for this card, as it's an R500 part. It's the "RadeonHD" (R600/R700) cards that don't have open-source 3D at the moment (it's under development).

My bad, sorry. Looked wrong on the [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver).

I overlooked: > X1050 / rv370 based cards
X1300 / R515 based cards
X1600 / R530 based cards
X1800 / R520 based cards
X1900 / R580 based cards

and focused on:
> ....
Xpress 1250 / AMD 690G / RS690 IGP
Xpress 1250 / AMD M690 / RS690M IGP
Xpress 1250 / AMD 690G / RS600 IGP for Intel
Xpress 1270 / AMD M690T / RS690T IGP

---

### Post by xZachtmx on 2009-06-06
Ok... I have done this to my /media/disk/etc/x11/xorg.conf

Section "Files"
    RgbPath    "/usr/X11R6/lib/X11/rgb"
    FontPath    "/usr/share/fonts/misc/"
    FontPath    "/usr/share/fonts/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/Type1/"
    FontPath    "/usr/share/fonts/TTF/"
    FontPath    "/usr/share/fonts/75dpi/"
    FontPath    "/usr/share/fonts/100dpi/"

#    ModulePath    "/usr/X11R6/lib/modules"

EndSection

Section "Module"

# This loads the DBE extension module.
    Load        "glx"
    Load    "dbe"
    
    SubSection    "extmod"
    Option    "omit xfree86-dga"
    EndSubSection
   
    Load    "type1"
    Load    "freetype"

EndSection

Section "ServerFlags"

# Set the basic blanking screen saver timeout.

    Option    "blank time"    "10"    # 10 minutes

# Set the DPMS timeouts.  These are set here because they are global
# rather than screen-specific.  These settings alone don't enable DPMS.
# It is enabled per-screen (or per-monitor), and even then only when
# the driver supports it.

    Option    "standby time"    "20"
    Option    "suspend time"    "30"
    Option    "off time"    "60"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier    "Keyboard1"
    Driver    "kbd"

# Set the keyboard auto repeat parameters.  Not all platforms implement
# this.

    Option    "AutoRepeat"    "1000 50"

# These are the default XKB settings for xorg

    Option    "XkbModel"    "pc104"
    Option    "XkbLayout"    "us"
#    Option    "XkbVariant"    ""
#    Option    "XkbOptions"    ""

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier    "Mouse1"
    Driver    "mouse"

    Option    "Protocol"    "IMPS/2"
    Option      "ZAxisMapping"  "4 5"

EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

Section "Monitor"

    Identifier    "Generic Monitor"
    HorizSync    30 - 85
    VertRefresh    50 - 160
    Option    "dpms"

EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

Section "Device"
         Identifier     "Radeon"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
EndSection


# **********************************************************************
# Screen sections.
# **********************************************************************

Section "Screen"

# The Identifier, Device and Monitor lines must be present

    Identifier    "Screen 1"
    Device    "Radeon"
    Monitor    "Generic Monitor"
    DefaultDepth 24

    SubSection "Display"
        Depth        24
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
#        ViewPort    0 0
#        Virtual     800 600
    EndSubsection

    SubSection "Display"
    Depth        16
        Modes        "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection

    SubSection "Display"
    Depth        8
        Modes        "1024x768" "800x600" "640x480"
    EndSubSection

EndSection


# **********************************************************************
# ServerLayout sections.
# **********************************************************************


Section "ServerLayout"
    Identifier    "simple layout"
    Screen    "Screen 1"
    InputDevice    "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection





but when i tested it by trying to turn on enhanced visual effects.. it says they cannot be enabled...  is the above all i need to do to load the graphics driver? or is there more (like something i gotta download)???

---

### Post by Yellow Pasque on 2009-06-06
Did you uninstall the fglrx drivers? IIRC:
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```
Also, make sure fglrx cleans up after itself:
```
sudo apt-get install --reinstall libgl1-mesa-glx
```

---

### Post by pricinosus on 2009-07-09
SO... nothing good here since the thread was started

I have radeon x1300, amd64, ubuntu 9.04 (amd64).

Problem: Can't change resolution above 800X600 (this is my first problem with display, sure a lot will come-compiz, dual display, tv out, etc)

Decided to change driver.

So.. i follow step by step [[COLOR="Red"]THIS[/COLOR]]("https://help.ubuntu.com/community/RadeonDriver") and after reboot ubuntu said "you... got to go low resolution, bla..bla.." and downgrade to original installation driver.

So.. I try [[COLOR="Red"]THIS[/COLOR]]("https://help.ubuntu.com/community/RadeonHD")
same s..t "you... got to go low resolution" and downgrade to original installation driver.

keep on fight and searched x.org site and found [[COLOR="Red"]THIS[/COLOR]]("http://www.x.org/wiki/radeonhd%3AINSTALL") again "you... got to go low resolution" and downgrade to original installation driver.


Is there a chance to install a working driver for ATI Radeon x1300, on amd64 machine with ubuntu amd64 ver 9.04?

A working tutorial, something... a link with step by step installation of driver (working),... a GUI based installer something.... is a total anarchy with this radeon cards and Ubuntu 9.04

I g00gled and nobody saied :yes my radeon x1300 card work with ubuntu9.04.

Are people here saying that?

Tell me, please how did you manged to make x1300 and ubuntu 9.04 work.

I use only ubuntu as OS from three years ago and the Internet and forums were my solutions for problems that I have to ubuntu.

But not today.... is anarchy

Please help me, I'm poor and don't have money to buy Windows 7 :grin:

search the forum :
[http://ubuntuforums.org/search.php?searchid=61534729](http://ubuntuforums.org/search.php?searchid=61534729)

Read :

[http://ubuntuforums.org/showthread.php?t=1166952&highlight=9.04+radeon+x1300+amd64](http://ubuntuforums.org/showthread.php?t=1166952&highlight=9.04+radeon+x1300+amd64)
[http://ubuntuforums.org/showthread.php?t=1175470&highlight=9.04+radeon+x1300+amd64](http://ubuntuforums.org/showthread.php?t=1175470&highlight=9.04+radeon+x1300+amd64)
[http://ubuntuforums.org/showthread.php?t=1164945&highlight=9.04+radeon+x1300+amd64](http://ubuntuforums.org/showthread.php?t=1164945&highlight=9.04+radeon+x1300+amd64)
[http://ubuntuforums.org/showthread.php?t=1143740&highlight=9.04+radeon+x1300+amd64](http://ubuntuforums.org/showthread.php?t=1143740&highlight=9.04+radeon+x1300+amd64)
[http://ubuntuforums.org/showthread.php?t=1148541&highlight=9.04+radeon+x1300+amd64](http://ubuntuforums.org/showthread.php?t=1148541&highlight=9.04+radeon+x1300+amd64)


All ended dramatically, with no solution!!!!

Is this crap... amd/ati give free source code and documentation to x.org... ?!?!!? huh....

some years ago ATI has the same problem with release of their drivers for windows... bang... bang... slap... this is a "big sux"

---

### Post by Yellow Pasque on 2009-07-09
The X1300 should work "out-of-the-box" without modification or changing drivers from the default xserver-xorg-video-radeon driver. It should also work with the "radeonHD" driver. I used to use this card and only had very minor issues with the radeon driver (they cleared up by using radeonhd).
First, boot the LiveCD (if you have it) to verify that the problem is with Ubuntu and not something you did.
If that works, reboot into your current install and run this to make sure you have the default xorg.conf:
```
sudo dpkg-reconfigure xserver-xorg
```
Restart X (log out or reboot). If you're still having resolution problems, post your /var/log/Xorg.0.log file.

To Zacht: run this command to make sure fglrx didn't leave the proprietary copy of libglx.so behind (because that will screw up compiz).
```
sudo apt-get --reinstall install xserver-xorg-core
```

---

### Post by pricinosus on 2009-07-10
Thank you Temüjin I will try later and post results here.

Thank you

---

### Post by NormanFLinux on 2009-08-03
Use the open source ati radeon driver and edit your xorg.conf file to force Ubuntu to recognize and boot up with it. The proprietary drivers don't work with 9.04.

---

