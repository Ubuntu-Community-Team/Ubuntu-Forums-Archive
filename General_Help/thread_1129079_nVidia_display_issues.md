---
title: "nVidia display issues"
date: 2009-04-18
forum: General Help
---

### Post by shut_down on 2009-04-18
Alright... I'm tired of fighting this thing, so here it is:

I have an older eMachine desktop, 1G RAM, AMD Sempron processor, and a 100GB HD.

At one point, I had my computer dual-booting into Windows XP and Ubuntu just fine... everything worked for both OS. Unfortunately, I ran into some problems, and had to totally format my hard drive and start over.

I got Windows XP back on it just fine... I even got Ubuntu back on it alright... but when I install the latest nVidia graphics driver, things get a little weird.

First off, the login screen doesn't even show up, simply a blank screen. I hear the little startup sound. I can type my username and password in and it will log into the desktop... at this point, the monitor will finally display a desktop.

Finally, if I set my monitor to display it's 1280x1024, the screen goes blank... in fact, I can't set it any higher than some odd resolution like 986x768 or something (I don't know specifically what it is, but I've not seen that resolution before)

What gets me is that it worked fine before I formatted my hard drive. I'm doing all the same stuff with it, so I don't know what the problem is.  I've edited my xorg.conf file so many times it's not even funny, and the Ctrl Alt +/- doesn't switch through the available resolutions like it should either. Any ideas?

(I'm away from my desktop right now, so if you need specifics like the contents of my xorg.conf file, it may be a little later on today)

---

### Post by CatKiller on 2009-04-18
Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```Bear in mind that these are the values for **my** monitor. You'll need to put in the values for **your** monitor, otherwise you could well permanently damage your monitor.

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-95
        VertRefresh     50-160
EndSection

```

---

### Post by shut_down on 2009-04-18
> **CatKiller said:**
> Normally, resolution problems are caused by one of the monitor, the graphics card, or the graphics driver not passing the EDID information to X that lets it automatically set the correct refresh rate, and so it defaults to really low values that won't damage any monitors. You can manually set the values for your monitor by putting the VertRefresh and HorizSync ranges in your xorg.conf. You should be able to get these numbers from the manual or specifications for your monitor. These values go in the "Monitor" Section of xorg.conf.

You can edit xorg.conf with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```Bear in mind that these are the values for **my** monitor. You'll need to put in the values for **your** monitor, otherwise you could well permanently damage your monitor.

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-95
        VertRefresh     50-160
EndSection

```

Ok, I've looked at my documentation that came with my monitor... I'm not sure what HorizSync and VertRefresh are.

My documentation has this list in it:
```

VGA 720 x 400 @ 70Hz
VGA 640 x 480 @ 60Hz
MAC 640 x 480 @ 67Hz
VESA 640 x 480 @ 75Hz
VESA 800 x 600 @ 56Hz
VESA 800 x 600 @ 60Hz
VESA 800 x 600 @ 72Hz
VESA 800 x 600 @ 75Hz
MAC 832 x 624 @ 75Hz
VESA 1024 x 768 @ 60Hz
VESA 1024 x 768 @ 70Hz
VESA 1024 x 768 @ 75Hz
VESA 1280 x 1024 @ 60Hz
VESA 1280 x 1024 @ 75Hz
```

and this:

```
Displayable Resolution: SXGA 1280 x 1024 max. Vertical Frequency 75Hz max.
```

It also labels the pixel dimension and Active Display Area, but those terms aren't really listed anywhere (I'm assuming VertRefresh would be the vertical frequency... so the VertRefresh would be 60-75)

EDIT: What gets me the most about this is that it worked fine before I formatted my drive, and now it doesn't. The only hardware I've installed has been a new sound card and a TV tuner, so I don't see how that would mess anything up.

---

### Post by CatKiller on 2009-04-18
> **shut_down said:**
> (I'm assuming VertRefresh would be the vertical frequency... so the VertRefresh would be 60-75)

Something like that. Have you got a model number? It might be possible to get the ranges from a Windows driver. Actually, it might be possible to get the ranges from Windows. I think most monitor drivers put them as a value in the registry somewhere. Can't remember off the top of my head exactly where though.

---

### Post by shut_down on 2009-04-18
> **CatKiller said:**
> Something like that. Have you got a model number? It might be possible to get the ranges from a Windows driver. Actually, it might be possible to get the ranges from Windows. I think most monitor drivers put them as a value in the registry somewhere. Can't remember off the top of my head exactly where though.

JC199D Hanns-G 19" monitor...

I'm guessing you don't really know why I'm suddenly having so much trouble with it this time around? Not that's it's important, I'm just really curious now.

---

### Post by CatKiller on 2009-04-18
> **shut_down said:**
> JC199D Hanns-G 19" monitor...

According to the Windows driver from the Hanns.G website, the range you're looking for is ```
HorizSync     30-83
VertRefresh     50-76
```
I think. Potentially the other way round.
> 
I'm guessing you don't really know why I'm suddenly having so much trouble with it this time around? Not that's it's important, I'm just really curious now.

Not a clue. Sorry. There have been some major changes to X over the last few releases. Was your install an upgrade from an earlier one, with this one a fresh install? That's the only thing I can think of.

---

### Post by shut_down on 2009-04-18
> **CatKiller said:**
> According to the Windows driver from the Hanns.G website, the range you're looking for is ```
HorizSync     30-83
VertRefresh     50-76
```
I think. Potentially the other way round.


Not a clue. Sorry. There have been some major changes to X over the last few releases. Was your install an upgrade from an earlier one, with this one a fresh install? That's the only thing I can think of.

Well, the first time (a couple months ago) I installed 8.10 and then updated it. Almost immediately, I started having problems, so I formatted my hard drive, and tried to reinstall windows... only to find out it was a RAM issue (I had bought some supposedly new RAM about the same time). I have just now gotten back around to reinstalling 8.10 from the same disk I used last time, and all this stuff starts happening.

---

### Post by CatKiller on 2009-04-18
> **shut_down said:**
> Well, the first time (a couple months ago) I installed 8.10 and then updated it. Almost immediately, I started having problems, so I formatted my hard drive, and tried to reinstall windows... only to find out it was a RAM issue (I had bought some supposedly new RAM about the same time). I have just now gotten back around to reinstalling 8.10 from the same disk I used last time, and all this stuff starts happening.

The only other thing I can think of, then, is that you're using a different driver version than before. Or gremlins.

---

### Post by shut_down on 2009-04-18
Okay... my resolution now works just fine under the default driver, but I would still like to use the nvidia one...

After booting under the default driver, I went to the prompt and did:

```
sudo nvidia-xconfig
```

and then rebooted. I am getting an "Out of Range" message from my monitor, which isn't new... when I changed the resolution the first time, this is what happened...

Is there a way I can keep the nvidia driver, but change the resolution to something safe so I can perhaps see what's going on?

---

### Post by shut_down on 2009-04-18
> **CatKiller said:**
> The only other thing I can think of, then, is that you're using a different driver version than before. Or gremlins.

Must be gremlins... although, nvidia did come out with a new driver, and I used that one first... however, when it didn't work, I would boot under the default driver, activate the next older nvidia driver, then reboot. Every driver gave me the same thing.

---

### Post by shut_down on 2009-04-18
Okay... I went into the xorg.config file and changed the driver name from "nvidia" to "nv", the default driver. I log in and everything works fine except I don't have all my little bells and whistles. I go System > Administration > Hardware Drivers, and it shows me that the latest nvidia driver is installed an activated...

However, when I go to System > Administration > NVIDIA X Server Settings, it tells me I need to do the "sudo nvidia-xconfig" thing again... and I still can't seem to get the desktop effects to work...

---

### Post by CatKiller on 2009-04-18
> **shut_down said:**
> Is there a way I can keep the nvidia driver, but change the resolution to something safe so I can perhaps see what's going on?

Yes, probably.

It's been a long time since I configured my graphics, but I seem to recall that nvidia-xconfig was pretty heavy-handed with changing xorg.conf. In reality, it only needs to put in two lines. In fact, I'm not entirely convinced that it's necessary to run nvidia-xconfig any more - I suspect that just installing the driver through System -> Administration -> Hardware Drivers and restarting X is sufficient.

It should be possible to press Ctrl-Alt-F1 to get into a virtual console (text-based) that will let you check what's happened to your xorg.conf. No gedit on the command-line, but nano is a good ncurses-based text editor; ```
sudo nano /etc/X11/xorg.conf
```should let you edit the file. Hopefully you'll just need to put the refresh rate lines back in.

Otherwise, Ctrl-Alt-+/- should raise/lower the resolutions through X's list of available modes.

---

### Post by shut_down on 2009-04-18
> **CatKiller said:**
> Yes, probably.

It's been a long time since I configured my graphics, but I seem to recall that nvidia-xconfig was pretty heavy-handed with changing xorg.conf. In reality, it only needs to put in two lines. In fact, I'm not entirely convinced that it's necessary to run nvidia-xconfig any more - I suspect that just installing the driver through System -> Administration -> Hardware Drivers and restarting X is sufficient.

It should be possible to press Ctrl-Alt-F1 to get into a virtual console (text-based) that will let you check what's happened to your xorg.conf. No gedit on the command-line, but nano is a good ncurses-based text editor; ```
sudo nano /etc/X11/xorg.conf
```should let you edit the file. Hopefully you'll just need to put the refresh rate lines back in.

Otherwise, Ctrl-Alt-+/- should raise/lower the resolutions through X's list of available modes.

Actually, that's how I've been editing the xorg.config file all along... but anyway.

The Ctrl Alt +/- doesn't seem to work very well... I've only been able to see it happen once, but neither resolution worked anyway...

I'm going to try again, though...

EDIT: My computer makes no effort to change the resolution with the ctrl alt +/- combo

---

### Post by CatKiller on 2009-04-18
> **shut_down said:**
> Okay... I went into the xorg.config file and changed the driver name from "nvidia" to "nv", the default driver. I log in and everything works fine except I don't have all my little bells and whistles. I go System > Administration > Hardware Drivers, and it shows me that the latest nvidia driver is installed an activated...

However, when I go to System > Administration > NVIDIA X Server Settings, it tells me I need to do the "sudo nvidia-xconfig" thing again... and I still can't seem to get the desktop effects to work...

It seems like you've now got a hybrid between a fully-automatic configuration and a manual one. You have a choice as to how you proceed, depending on whether you want to return to automatic settings, or manually tune your xorg.conf. There's nothing wrong with having a manual xorg.conf; mine is still the carefully hand-crafted xorg.conf that I made when I was running Dapper. But a fully-automatic xorg.conf doesn't have a Driver line. At all. It's all Default this and Configured that.

If you do go for the manual route, and you don't want nvidia-xconfig to mangle your xorg.conf, the changes that it is supposed to make are to put the Driver to "nvidia," remove the "GLcore" and "dri" modules, and load the "glx" module.

Here's mine, for comparison.

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "dbe"
    Load    "ddc"
#    Load    "dri"
#SubSection "extmod"
#    Option    "omit MIT-SCREEN-SAVER"
#EndSubSection
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "record"
#    Load    "type1"
    Load    "v4l"
    Load    "vbe"
#    Load    "GLcore"

EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
#    Option        "Protocol"        "ExplorerPS/2"
    Option        "Protocol"        "auto"
    Option        "ZAxisMapping"        "4 5"
    Option        "Emulate3Buttons"    "False"
    Option        "Buttons"        "7"
    Option        "ButtonMapping"        "1 2 3 6 7"
    Option        "Resolution"        "2000"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "nVidia Corporation NV44A [GeForce 6200]"
    Driver        "nvidia"
    BusID        "PCI:0:8:0"
    Option        "NoLogo"
#    Option        "AllowGLXWithComposite"        "True"
#    Option        "AddARGBGLXVisuals"        "True"
    Option        "UseEDID"            "False"
    Option        "CoolBits"            "1"
EndSection

Section "Monitor"
    Identifier    "Eizo F77"
    Option        "DPMS"
    HorizSync    30-95
    VertRefresh    50-160
    DisplaySize    402 300
    Gamma        1.15
EndSection

Section "Screen"
    Identifier    "Left Screen"
    Device        "nVidia Corporation NV44A [GeForce 6200]"
    Monitor        "Eizo F77"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1600x1200" "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1600x1200" "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1600x1200" "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1600x1200" "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1600x1200" "1280x1024" "1024x768"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1600x1200" "1280x1024" "1024x768"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen 0    "Left Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice     "stylus"    "SendCoreEvents"
#    InputDevice     "cursor"    "SendCoreEvents"
#    InputDevice     "eraser"    "SendCoreEvents"
EndSection

#Section "DRI"
#    Mode    0666
#EndSection
```

---

### Post by CatKiller on 2009-04-18
> **shut_down said:**
> My computer makes no effort to change the resolution with the ctrl alt +/- combo

**xrandr** is the current command-line tool to change the resolution. Can't remember exactly what the options are though. **man xrandr** will hopefully tell you how.

---

### Post by shut_down on 2009-04-18
> **CatKiller said:**
> **xrandr** is the current command-line tool to change the resolution. Can't remember exactly what the options are though. **man xrandr** will hopefully tell you how.

Using xrandr gives me this:

```
Can't open display
```

---

### Post by shut_down on 2009-04-18
Here is my xorg.config file (Starting after all the introductory stuff):

```
Section "Monitor"
Identifier     "Configured Monitor"
HorizSync      31.0-80.0
VertRefresh    55.0-75.0
EndSection

Section "Screen"
Identifier     "Default Screen"
Device         "Configured Video Device"
Monitor        "Configured Monitor"
Option         "UseDisplayDevice" "DFP"
Option         "NoLogo" "True"
DefaultDepth   "24"
Subesection "Display"
     Depth     24
     Modes     "nvidia-auto-select"
EndSubsection
EndSection

Section "Module"
Load           "glx"
EndSection

Section "InputDevice"
Identifier     "Mouse0"
Driver         "mouse"
Option         "Protocol" "auto"
Option         "Device" "/dev/psaux"
Option         "Emulate3Buttons" "no"
Option         "ZAxisMapping" "4 5"
EndSection

Section "ServerLayout"
Identifier     "Default Layout"
Screen         "Default Screen" 0 0
InputDevice    "Keyboard0" "CoreKeyboard"
InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
Identifier     "Configured Video Device"
Driver         "nvidia"
Option         "NoLogo" "True"
EndSection

```

What do I need to this file?

---

### Post by shut_down on 2009-04-18
I notice in your xorg.conf file you have a line indicating that you would not like to use the EDID. Should I disable that as well?

---

### Post by shut_down on 2009-04-18
Well, I formatted my Ubuntu partition and reinstalled it... This time, before even updating anything, I just activated the nVidia driver.

Same thing.

I don't know why, but I guess I'm just not meant to have Ubuntu with all its neat little effects on this computer.:(

---

### Post by CatKiller on 2009-04-18
> **shut_down said:**
> Using xrandr gives me this:

```
Can't open display
```

I hadn't researched it much, and didn't have time then. You can do quite a lot with xrandr, and I understand that it's the way that resolutions and multiple displays and the like are to be set in the new versions of X.

> **shut_down said:**
> I notice in your xorg.conf file you have a line indicating that you would not like to use the EDID. Should I disable that as well?

Probably not. I wasn't sure if I was getting incorrect EDID info, or none at all, so I told X to ignore whatever it had. It worked, so I stopped fiddling :)

> **shut_down said:**
> Well, I formatted my Ubuntu partition and reinstalled it... This time, before even updating anything, I just activated the nVidia driver.

Same thing.

What happens if you put just the HorizSync & VertRefresh lines in your xorg.conf now that it's pristine?

---

### Post by shut_down on 2009-04-18
> **CatKiller said:**
> I hadn't researched it much, and didn't have time then. You can do quite a lot with xrandr, and I understand that it's the way that resolutions and multiple displays and the like are to be set in the new versions of X.



Probably not. I wasn't sure if I was getting incorrect EDID info, or none at all, so I told X to ignore whatever it had. It worked, so I stopped fiddling :)



What happens if you put just the HorizSync & VertRefresh lines in your xorg.conf now that it's pristine?

Haha, nothing... The nvidia driver still doesn't work.

Do you think... The first time I had Ubuntu on my desktop, that was all that was there, meaning, I didn't have a dual-boot or anything. The only thing on my desktop was Ubuntu. Do you think that would make a difference? I honestly don't see why it would, but just wondering...

EDIT: OH WAIT HOLD ON!

I didn't put my refresh rates in quotes, so I went back and did that... for some reason, that made other things happen...

I got an error message saying that I am now operating in Low-Graphics mode because there's an error with my display settings. It is now giving me three choices:

Run Ubuntu in low-graphics mode
Reconfigure Graphics
Troubleshoot the error...

Any suggestions?

---

### Post by CatKiller on 2009-04-18
> **shut_down said:**
> Do you think... The first time I had Ubuntu on my desktop, that was all that was there, meaning, I didn't have a dual-boot or anything. The only thing on my desktop was Ubuntu. Do you think that would make a difference? I honestly don't see why it would, but just wondering...

I'm with you; I don't see how that could make a difference.

> I didn't put my refresh rates in quotes, so I went back and did that... for some reason, that made other things happen...

The refresh rate ranges shouldn't be in quotes, should they?

Some people seem to recommend modelines. They specify exact timings for each screen mode. I've never needed to use them, so I don't know anything about them, really. You might be able to find something though.

---

### Post by Shininggg on 2009-04-18
this is the only reason why i went back to 8.04 :(

I'm no expert here, but from what i've read 8.10 ubuntu uses the latest Xorg.conf file format which the nvidia-xconfig has trouble to configure...

Believe me i'm the kinda guys who spends countless hour trying to fix those thing but this time i gave up and went back to 8.04 until the issue is fixed...

---

### Post by shut_down on 2009-04-18
I think I've given up on it for today... Thanks so much for your help, but I'll just try to figure something else out.

---

### Post by shut_down on 2009-04-20
So I think I may have figured out what happened, and it's mostly because I don't pay attention.

I made a post a while back asking for installation help on for Ubuntu on my laptop. Apparently, I was using the 8.04 disk on my laptop, and found that I needed the alternative 8.10 install. Without thinking, I threw away my old 8.04 disk, since 8.10 is newer... Since that was a while back, I had just forgotten that I ever had an 8.04 disk.

In other words, the first time I installed Ubuntu, it was with an 8.04 disk, so that was the change I had incurred between the two installs.

Thanks for everyone's help... It'd be nice if we could get a solid solution on this, but we can just deal, I guess.

---

### Post by CatKiller on 2009-04-27
> **shut_down said:**
> I notice in your xorg.conf file you have a line indicating that you would not like to use the EDID. Should I disable that as well?

Actually, maybe. I just upgraded to Jaunty and I was having a fiddle. Commenting out that line meant that my monitor got correctly identified (yay!) but the highest mode wasn't available. I understand that it's possible to tell X to only ignore some EDID information, so that's what I'll be trying next.

---

### Post by CatKiller on 2009-04-27
Gah. Using the ModeDebug option in xorg.conf let me see what EDID the monitor was actually reporting, and it's nothing like what the monitor can do. Back to UseEDID=False for me. But looking at the specs again meant that I noticed my monitor can do 1600×1200@75 rather than the 1600×1200@60 that I was using before, so I calculated the dot clock for that and put that in too.

---

