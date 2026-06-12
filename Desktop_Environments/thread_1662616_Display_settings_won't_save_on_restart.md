---
title: "Display settings won't save on restart"
date: 2011-01-08
forum: Desktop Environments
---

### Post by animedragon67 on 2011-01-08
So I had this issue before updating to 10.10 and it persisted after the upgrade. I have a dual monitor setup. Each time I log in from a restart I have to tell it not be be a clone of the first and that it's to the left, as well as change it's resolution. Now with 10.10 and activities I have to switch that as well.
I have a dual boot of kubuntu and windows, so it's really annoying to have to set this up every time I come back. I've had a friend suggest there might be a config file somewhere that I could add a line to.

---

### Post by inobe on 2011-01-08
open terminal/konsole and try

```
kdesudo nvidia-settings
```

if you have an nvidia card!


that will give you the admin privileges to save the setup to nvidia xconfig.

---

### Post by animedragon67 on 2011-01-09
So I entered that line and it gave me the error message "You do not appear to be using NVIDIA X driver. Please edit your x configuration file" so I tried to run 'nvidia-xconfig' but the only thing that happened is an error message that quits immediately so I couldn't tell you what it's for.
seems like maybe if I get that working there might be a solution?

---

### Post by pgibson on 2011-01-09
I'm glad you mentioned this.  This morning I just installed kubuntu 10.04.1 on a computer, turned it off, moved it downstairs and connected it to another, different monitor and Ugh, wrong resolution!  I haven't turned it off since then.  I'm hoping it's not permanent-ish.

I did a non-technical "fix" on my xubuntu 10.10 box when this happened.  I turned off the machine, then turned off the monitor, then turned on the machine again and when I turned on the monitor again, voila!  Correct resolution.  I do a similar trick whenever my usb wireless dongle has been removed and reinstalled too.  Probably won't fix things, but it's pretty easy and quick to find out that it doesn't work. ;)

Oh, maybe try powering down and unplugging one of the monitors and leaving it unplugged while powering up again.  Again, painless, and maybe you'll get lucky.

I'm going to try powering down my kde machine now, see if I have a recurring problem as well.

---

### Post by animedragon67 on 2011-01-09
Interesting. My computer hardly ever goes off, the only cases being if I'm going to be away for a weekend or a trip which has only happened on occasion. Though I believe the monitors were on before I powered up the computer.
One of my monitors is a VGA and the other bigger better one is a DVI, seems that the computer decides that VGA connections come before DVIs so it uses the VGA resolution.

---

### Post by Krytarik on 2011-01-09
> **animedragon67 said:**
> So I entered that line and it gave me the error message "You do not appear to be using NVIDIA X driver. Please edit your x configuration file" so I tried to run 'nvidia-xconfig' but the only thing that happened is an error message that quits immediately so I couldn't tell you what it's for.
seems like maybe if I get that working there might be a solution?
Do you have a Nvidia card/chip then, and the proprietary driver installed?
If not, forget about that way.

First try to specify the monitor modes via "/etc/X11/xorg.conf", if that doesn't work specify them with "xrandr" via the desktop startup scripts:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by pgibson on 2011-01-09
animedragon67, for what it's worth, it did just work for me to start the monitor after the machine.  First I tried just leaving the monitor on and restarting the machine. That resulted in GIGANTIC KDE RESOLUTION. (Ick.) The second time I shut down the machine and shut off the monitor before starting the machine back up.  (I waited a bit till I felt the machine was possibly at the login screen, and then turned on the monitor.)

There were a few blinks, but then all was normal, pretty resolution.  I'm so proud, my little kde is getting all grown up.  (sniff).  It figured out the resolution all by its ittle self.

Now if it will just save it and know what the monitor is when it restarts, all will be kisses and hugs, violets and butterflies.

Interested to what you find.

---

### Post by animedragon67 on 2011-01-09
ok so it appears I was mistaken, I'm not sure how, but I have an ati radeon card not nvidia card.
I had installed it from the windows side, but apparently I must need to install it on the linux side as well, only the cd doesn't run with linux so I downloaded the propriety driver from online.

I'm attempting to go through some startup script and edit them if I can find the correct one that does that and add in some lines, however I don't really know at this point which it is. I did find one at etc/X11/ called default-display-manager. The only thing written in it is /usr/bin/kdm.

---

### Post by Krytarik on 2011-01-09
Please read/follow the guide carefully.

In your case, the files concerning both possible ways are
- for xorg.conf: /etc/X11/xorg.conf
- for xrandr: /etc/kde4/kdm/Xsetup

You should also make sure that you run the best possible/correct video driver.
Check in the KDE-equivalent of "System -> Administration -> Additional Drivers", if it offers you a proprietary driver for your card/chip.

If you have an older ATI card/chip, which isn't supported by the proprietary drivers anymore, the Open Source Edge Drivers are currently the best solution:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)
(look below that section to get to a list of now unsupported video cards/chips)

---

### Post by animedragon67 on 2011-01-13
II should mention that I'm still learning how to use linux terminal so I don't really know how to use xrandr, I have made changes in some files before using kate but there was already things written in the file and all I had to do was change a few words.
Greatly appreciated if it could be explained to me how exactly I should use xrandr to make these changes.

I have looked around and cannot for the life of me find the equivalent of "System -> Administration -> Additional Drivers". Even did a search online and didn't find anything.

---

### Post by Krytarik on 2011-01-14
I found this path in the web:
> You can enable these drivers by opening up the [K] menu , selecting "Applications", then "System", and start the "Additional drivers" application to install the nvidia drivers.
Hope it helps.

---

### Post by animedragon67 on 2011-01-15
ok so going to additional drivers allowed me to install the propriety drivers I needed, as well as renamed VGA and DVI to CRT and DFP. 
However now I have almost a worse problem: once I restarted the computer and came back it wouldn't change the resolution to anything above my smaller VGA monitor and is stuck on clone, even if I tell it to be right of the VGA one.
It's a bit weird, the options to change it to 1950x1080 are there but when I select it nothing happens and it changes back to the lower one.

This is really sucking since now I basically am back to having only one monitor unless I disable the drivers which I am considering doing if this goes on for too long. Not only is it back to one monitor but my smaller one.

Ok so I can get the monitor to stop being a clone if I have it on the lowest resolution possible which is useless (640x480) or with playing around can get it at it's proper resolution and turn my other one into the lowest, which is what I'm keeping it at for now until it gets figured out.

---

### Post by Krytarik on 2011-01-16
The proprietary driver for ATI/AMD cards/chips comes also with its own configuration tool, it's called "AMD Catalyst Control Center" (according to its website, may be also ATI ...). It should be in the "System" menu also. Try to set up your configuration with those tool, if you haven't done that already.

If that doesn't work, you should really try to set up the monitor modes in one of those ways.
> **Krytarik said:**
> 
First try to specify the monitor modes via "/etc/X11/xorg.conf", if that  doesn't work specify them with "xrandr" via the desktop startup  scripts:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)
It's really not that difficult. You have now the "xorg.conf" at least set up to your current driver and its options, you only have to fix the modes, and if that way also doesn't work, the xrandr way should.

Good luck!

---

### Post by animedragon67 on 2011-01-16
Ok this is not good. 
I configured the AMD catalyst control center and it required a restart. It got to the point after I chose the operating system to boot up and then blank screen.
After a couple attempts with the same result I came into windows.
:(

---

### Post by Krytarik on 2011-01-16
Then try to boot into "recovery mode", choose "root shell prompt", and then enter:
```
sudo aticonfig --initial -f
```
Then reboot. There is another command in this guide to set up dual monitor config:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Generate_a_new_.2Fetc.2FX11.2Fxorg.conf_file)
```
sudo aticonfig --initial -f --adapter=all
```

---

### Post by Edoaigor on 2011-01-16
I have a major display issue on an old HP OmniBook with a Pentium 3 900 Mhz processor I'm tried to install Xubuntu on. I managed the install starting from the minimal iso and installing the xubuntu package with tasksel. The problem is the screen is not correctly set unless I run in Gnome Safe Graphics mode (had to install that too.. could not see anything on my xserver otherwise) I tried running in safe mode and it worked the first time, but after fiddling around and rebooting the screen started being  garbled even in safe mode.
If I start a Xubuntu session all i see is the default wallpaper (no menus, no icons whatsoever). If I choose the xfce terminal session I get the same result plus a terminal window which is way bigger than the screen (I don't get to see the upper left corner of it). Tried changing resolution, scale, mode whatever using xrandr but I could only get the text bigger or smaller... and see less of the terminal window. I'm puzzled..

---

### Post by Krytarik on 2011-01-16
@Edoaigor: It would be better to start a new thread on your matter, not at least to draw more attention. 

About your issue: I had a conversation recently with another user regarding a similar issue with an old Omnibook, maybe you can get some usefull tips out of it:
[http://ubuntuforums.org/showthread.php?t=1663355](http://ubuntuforums.org/showthread.php?t=1663355)

---

### Post by animedragon67 on 2011-01-16
So I've been trying to follow the guides and create a new xorg.conf file..I edited Xsetup but it didn't seem to change anything. I was following this guide:
[https://wiki.archlinux.org/index.php/Xorg](https://wiki.archlinux.org/index.php/Xorg)

I couldn't tell you what I'm doing wrong, but I'll post what I wrote. My guess would be naming things for one.

Section "ServerLayout"
    Identifier    "DualScreen"
    Screen       0 "DFP2"   
    Screen       1 "CRT2" RightOf "DFP2" #Screen1(CRT2) right of Screen0(DFP2)
    Option         "Xinerama" "1" #To move windows between screens
EndSection

Section "Monitor"
    Identifier    "Monitor0"
    Option        "Enable" "true"
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    Option        "Enable" "true"
EndSection

Section "Device"
    Identifier    "Device0"
    Driver        "ati" #Choose the driver used for this monitor
    Screen        0
EndSection

Section "Device"
    Identifier    "Device1"
    Driver        "ati"
    Screen        1
EndSection

Section "Screen"
    Identifier    "Screen0"  #Collapse Monitor and Device section to Screen section
    Device        "Device0" 
    Monitor       "Monitor0"
    DefaultDepth  24 #Choose the depth (16||24)
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

---

### Post by Krytarik on 2011-01-16
```
Section "ServerLayout"
    Identifier    "DualScreen"
    Screen       0 "DFP2"   
    Screen       1 "CRT2" RightOf "DFP2" #Screen1(CRT2) right of Screen0(DFP2)
    Option         "Xinerama" "1" #To move windows between screens
EndSection

Section "Monitor"
    Identifier    "Monitor0"
    Option        "Enable" "true"
EndSection

Section "Monitor"
    Identifier    "Monitor1"
    Option        "Enable" "true"
EndSection

Section "Device"
    Identifier    "Device0"
[COLOR=Red]     Driver        "ati" #Choose the driver used for this monitor[/COLOR]
    Screen        0
EndSection

Section "Device"
    Identifier    "Device1"
[COLOR=Red]     Driver        "ati"[/COLOR]
    Screen        1
EndSection

Section "Screen"
    Identifier    "Screen0"  #Collapse Monitor and Device section to Screen section
    Device        "Device0" 
    Monitor       "Monitor0"
    DefaultDepth  24 #Choose the depth (16||24)
    SubSection "Display"
        Depth     24
    EndSubSection
EndSection

```
It's a good start, but

- "ati" would mean the default open source driver, not the proprietary one, those is called "fglrx"

- it may be necessary to add the specs of your monitor, I add my xorg.conf below for reference. To get the correct values of your monitor, use hwinfo:
```
sudo apt-get install hwinfo
sudo hwinfo --monitor
```

- you have to add another "Screen" section, like in this example:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)

- you should specify the desired monitor modes also, in the screen sections, like in the above example (if that doesn't work, you may have to add the according "modelines" to the "Monitor" sections)

You have to put all that in "/etc/X11/xorg.conf", not anywhere else, if that file doesn't exist, create it.
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Fri Apr  9 10:35:18 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Sony CPD-4401"
[COLOR=Red]    HorizSync       30.0 - 107.0
    VertRefresh     48.0 - 120.0
[/COLOR]    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 Ti 4200"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1152x864_85 +0+0; 1152x864 +0+0; 1152x864_100 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by animedragon67 on 2011-01-24
Ugh....so I've been procrastinating a bit but seems I'm having problems with creating the xorg.conf file, I've tried multiple times and it has a problem with the names of the horizontal/vertical syncs. I don't know what it would accept though. Eventually I erased it and booted back up to what I had before so I could do something other than terminal.
Do things have different names according to the versions or computer you have?
Or if there's a better way I can fix this problem.

---

### Post by Krytarik on 2011-01-24
> **animedragon67 said:**
> 
Do things have different names according to the versions or computer you have?
Or if there's a better way I can fix this problem.
No, not regarding the monitor specs, at least as far as I know.

You could also try the "xrandr" way described in the guide I posted earlier:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by mynevdull on 2012-03-06
AMD Radeon solution for me:

In short, sometimes (e.g. in my case) my user's .kde settings were overruling the system settings set by the AMD Catalyst Control Center app in Debian Squeeze kde.

Symptom: Login screen had dual monitors working correctly, but weren't working correctly after logging in.  Changes via AMD Catalyst Control Center would revert following reboot - or re-login.

Resolution: 
a) rm -rf $HOME/.kde
b) comment out xrandr setting in $HOME/.kde/share/config/*

-M

---

