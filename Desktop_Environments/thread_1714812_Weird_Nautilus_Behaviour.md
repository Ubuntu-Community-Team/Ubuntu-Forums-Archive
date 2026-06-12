---
title: "Weird Nautilus Behaviour"
date: 2011-03-25
forum: Desktop Environments
---

### Post by peshko-lnx on 2011-03-25
EVERY SINGLE TIME when I try to close the Nautilus File Browser (ie when I go to my Documents folder), the desktop flashes all the icons on the desktop a couple of times (for a sec you would see no icons on the desktop) before everything goes back to normal.

WHY IS THAT and how can I fix it?

(Ubuntu 10.10 64-bit and Nautilus 2.32.0)

---

### Post by Krytarik on 2011-03-25
I remember experiencing the same behaviour before I properly configured my Nvidia driver.

Do you have a Nvidia card/chip? Are you running the proprietary driver?

---

### Post by peshko-lnx on 2011-03-25
Correct. nVidia. I use the nvidia-current drivers from the repo.

---

### Post by peshko-lnx on 2011-03-25
I just looked at nVidia settings...nothing in particular. DO you remember what you configured?

---

### Post by peshko-lnx on 2011-03-25
nvidia-current - 270.29

---

### Post by Krytarik on 2011-03-25
Check for the following option in the "Screen" section of your "/etc/X11/xorg.conf", and if it's not there, add it:
```
Option         "AddARGBGLXVisuals" "True"
```And since we are already talking about the driver, you may upgrade through Xorg-Edgers' PPA, it offers more recent drivers than the offical repos:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by peshko-lnx on 2011-03-25
I just followed your suggestions, and still the same behaviour. Got the new ppa upgraded, still the same. I tried downgrading the nvidia-current, but to no avail.

Anything else you may think of?

---

### Post by peshko-lnx on 2011-03-25
BTW I have an error on ia-32, but I don't think that would make a difference.

---

### Post by peshko-lnx on 2011-03-25
You think this has nothing to do with Gnome Nautilus? I have some weird gnome behaviour I have another question posted :

[http://ubuntuforums.org/showthread.php?t=1714492](http://ubuntuforums.org/showthread.php?t=1714492)

---

### Post by Krytarik on 2011-03-25
> **peshko-lnx said:**
> I just followed your suggestions, and still the same behaviour. Got the new ppa upgraded, still the same. I tried downgrading the nvidia-current, but to no avail.

Anything else you may think of?
I assume you at least relogged in after that!?
> **peshko-lnx said:**
> BTW I have an error on ia-32, but I don't think that would make a difference.
What exactly do you mean by that?
> **peshko-lnx said:**
> You think this has nothing to do with Gnome Nautilus? I have some weird gnome behaviour I have another question posted :

[http://ubuntuforums.org/showthread.php?t=1714492](http://ubuntuforums.org/showthread.php?t=1714492)
Are you running vanilla Nautilus or Nautilus Elementary?

---

### Post by peshko-lnx on 2011-03-25
> **Krytarik said:**
> I assume you at least relogged in after that!?

What exactly do you mean by that?

Are you running vanilla Nautilus or Nautilus Elementary?

I reboot.

When I try to upgrade ia-32, mid-point it says 

installArchives() failed: 
Preparing to replace ia32-libs 20090808ubuntu10~wineppa4 (using .../ia32-libs_20090808ubuntu10+maverick~xorgedgers0.20110325.1_amd64.deb) ... 
Unpacking replacement ia32-libs ... 
dpkg: error processing /var/cache/apt/archives/ia32-libs_20090808ubuntu10+maverick~xorgedgers0.20110325.1_amd64.deb (--unpack): 
 trying to overwrite '/lib32/libncursesw.so.5.7', which is also in package lib32ncursesw5 5.7+20100626-0ubuntu1 
No apport report written because MaxReports is reached already
dpkg-deb: subprocess paste killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/ia32-libs_20090808ubuntu10+maverick~xorgedgers0.20110325.1_amd64.deb 

Nautilus ot Nautilus Elementary? That is a good question. I never installed anything special. So I presume it is Nautilus. How can I verify?

Thanks a lot for your help, really! This thing is driving me nuts.

---

### Post by Krytarik on 2011-03-25
I don't think that it's related, can you lock its current version in Synaptic?
> **peshko-lnx said:**
> 
Nautilus ot Nautilus Elementary? That is a good question. I never installed anything special. So I presume it is Nautilus. How can I verify?

The current version of vanilla Nautilus for Maverick is: 2.32.0-0ubuntu1.3.
Those of Nautilus Elementary is: 2.32.2-0ubuntu2.

---

### Post by peshko-lnx on 2011-03-25
I run nautilus 2.32. Here is a screenshot...

---

### Post by Krytarik on 2011-03-25
> **Krytarik said:**
> I don't think that it's related, can you lock its current version in Synaptic?
With that I was actually referring to that:
> **peshko-lnx said:**
> 
When I try to upgrade ia-32, mid-point it says 

installArchives() failed: 
Preparing to replace ia32-libs 20090808ubuntu10~wineppa4 (using .../ia32-libs_20090808ubuntu10+maverick~xorgedgers0.20110325.1_amd64.deb) ... 
Unpacking replacement ia32-libs ... 
dpkg: error processing /var/cache/apt/archives/ia32-libs_20090808ubuntu10+maverick~xorgedgers0.20110325.1_amd64.deb (--unpack): 
 trying to overwrite '/lib32/libncursesw.so.5.7', which is also in package lib32ncursesw5 5.7+20100626-0ubuntu1 
No apport report written because MaxReports is reached already
dpkg-deb: subprocess paste killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/ia32-libs_20090808ubuntu10+maverick~xorgedgers0.20110325.1_amd64.deb 
I didn't consider it necessary to quote that all.

Please post your xorg.conf, in code-tags please, the #-button in the editor.

---

### Post by peshko-lnx on 2011-03-26
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Unknown"
        ModelName      "Unknown"
        HorizSync       28.0 - 33.0
        VertRefresh     43.0 - 72.0
        Option         "DPMS"
EndSection

Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth       24
        EndSubSection
        Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0" 0 0
        # commented out by update-manager, HAL is now used and auto-detects devices
        # Keyboard settings are now read from /etc/default/console-setup
        #    InputDevice    "Keyboard0" "CoreKeyboard"
        # commented out by update-manager, HAL is now used and auto-detects devices
        # Keyboard settings are now read from /etc/default/console-setup
        #    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
        Identifier     "Device0"
        VendorName     "NVIDIA Corporation"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection

```

---

### Post by peshko-lnx on 2011-03-26
I was just looking at the conf file. Noticed that the Monitor section it says unknown. I run Toshiba Tecra M10 laptop with nVidia Qudro NVS 150M.

This is waht nVidia Admin Settings suggest to put in the xorg.conf file:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@radon)  Fri Feb 25 17:16:21 UTC 2011

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Mouse0"
#    Driver         "mouse"
#    Option         "Protocol" "auto"
#    Option         "Device" "/dev/psaux"
#    Option         "Emulate3Buttons" "no"
#    Option         "ZAxisMapping" "4 5"
#EndSection
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

Section "ServerLayout"

    # commented out by update-manager, HAL is now used and auto-detects devices
    # Keyboard settings are now read from /etc/default/console-setup
    #    InputDevice    "Keyboard0" "CoreKeyboard"
    # commented out by update-manager, HAL is now used and auto-detects devices
    # Keyboard settings are now read from /etc/default/console-setup
    #    InputDevice    "Mouse0" "CorePointer"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Toshiba Internal LCD"
    HorizSync       54.0 - 56.0
    VertRefresh     59.0 - 61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 150M"
    Option         "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by peshko-lnx on 2011-03-26
Well, I even tried with the settings from the nVidia Xserver Settings admin tool. Still the same problem.

---

### Post by Krytarik on 2011-03-26
Before I forget to mention it, please stop posting in that frequency, at could be seen as inappropriate by other members to post 3-5 times in a row each time, you need to strike a balance between "posting" and "editing", but consider that the subscribed member don't get notified about "edits".

So, your xorg.conf is almost the same like mine, except
- hardware specific entries
- mine includes the chosen screen resolution
- yours include the "glx" module, mine not

You can shrink your xorg.conf safely into this:
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Option         "Xinerama" "0"
EndSection

[B][COLOR=Red]Section "Module"
    Load           "glx"
EndSection
[/COLOR][/B]
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Toshiba Internal LCD"
[B][COLOR=Red]    HorizSync       54.0 - 56.0
    VertRefresh     59.0 - 61.0
[/COLOR][/B]    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 150M"
    Option         "NoLogo" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```1.) Check if the monitor specs are correct, one of those ways should work:

a)```
sudo apt-get install hwinfo
hwinfo --monitor
```b)```
xvidtune
```press "Cancel"!

c) manual, web search

2.) Remove the "glx" module section

---

### Post by peshko-lnx on 2011-03-26
I applied your version of the xorg.conf.

Here is the output of the hwinfo:

```
peshko@my-lnx:~$ hwinfo --monitor
34: None 00.0: 10000 Monitor                                    
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 1024x768@76Hz
  Driver Info #0:
    Max. Resolution: 1024x768
    Vert. Sync Range: 50-90 Hz
    Hor. Sync Range: 31-61 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

and xvidtune

```
peshko@my-lnx:~$ sudo xvidtune
[sudo] password for probev: 
Vendor: Unknown, Model: Toshiba Internal LCD
Num hsync: 1, Num vsync: 1
hsync range 0:  54.00 -  56.00
vsync range 0:  59.00 -  61.00
```

I also removed 'glx' section. That did NOT help either. Still with the same issue - closing the file browser, flashes the desktop icons couple of times, before it brings them to the desktop permanently. Interestingly it does it only in the File Browser.

BTW, just fyi I have another weird thing that in the file browser and in ther Places I have two entries for the same mounted NFS disk. I have the entry in the fstab.

---

### Post by Krytarik on 2011-03-26
> **peshko-lnx said:**
> 
I also removed 'glx' section. That did NOT help either. Still with the same issue - closing the file browser, flashes the desktop icons couple of times, before it brings them to the desktop permanently. Interestingly it does it only in the File Browser.
Ok, there are different outputs of your monitor specs, the latter is reflected by your xorg.conf. You should try to get the correct values with a look into the manual or a web search. But in the end, it may not be related.
> **peshko-lnx said:**
> 
BTW, just fyi I have another weird thing that in the file browser and in ther Places I have two entries for the same mounted NFS disk. I have the entry in the fstab.
I know, but that's completely unrelated, and since I have no experience with NFS, I can't help you with it.

---

### Post by peshko-lnx on 2011-03-26
> **Krytarik said:**
> Ok, there are different outputs of your monitor specs, the latter is reflected by your xorg.conf. You should try to get the correct values with a look into the manual or a web search. But in the end, it may not be related.

I agree. Yesterday I moved from 10.04 to 10.10. I didn't have these issues in 10.04. I played with diff settings and resoultions in the past 20 min, but nothing helped.

> I know, but that's completely unrelated, and since I have no experience with NFS, I can't help you with it.

Sure. I just brought it, because I lean to believe that Nautilus might be the problem. And I am not sure if there is a ppa for nightly builds or something like that.

Thanks again for all your help!

---

### Post by Krytarik on 2011-03-26
Ah, forget to mention it: Nautilus also handles the desktop, that's the reason why you experience that behaviour only with Nautilus.

You may try using Nautilus Elementary instead, maybe it works for you, for me it doesn't, scrolling glitch:
[http://www.makeuseof.com/tag/nautilus-elementary-simplifies-file-browsing-linux/](http://www.makeuseof.com/tag/nautilus-elementary-simplifies-file-browsing-linux/)

**EDIT:** Forget about Nautilus Elementary! It came another thing into my mind: It wasn't actually about the mentioned option in xorg.conf, but about Metacity. May it be, that you really run Metacity, not Compiz, no desktop effects? If you want/need to stick with it, enable its option "/apps/metacity/general/compositing_manager" in "gconf-editor", that fixes those issue also.

---

### Post by peshko-lnx on 2011-03-26
Just installed Nautilus Elementary and everything works great.

Thanks again!

---

### Post by Krytarik on 2011-03-26
Did you see my remark about Metacity?
Which WM do you run then?

---

### Post by peshko-lnx on 2011-03-26
I ppa-purged Elementary. To be honest I am not sure if I run Metacity, but just in case enabled compositing_manager in gconf. Rebooted, and nothing. Still the same problem.

I even went to Appearance and disabled any effects. Still no luck.

---

### Post by Krytarik on 2011-03-26
Those behaviour only happens at my system when running Metacity (Visual Effects = "None") with its compositing option disabled.

---

### Post by peshko-lnx on 2011-03-26
I filed a bug - 743248. We'll see. For time being I'll work with Nautilus Elementary. It seems I have no issues with it.

Thanks again for your time and your help!

---

