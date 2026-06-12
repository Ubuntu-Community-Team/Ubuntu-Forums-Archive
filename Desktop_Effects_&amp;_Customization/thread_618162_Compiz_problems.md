---
title: "Compiz problems"
date: 2007-11-20
forum: Desktop Effects &amp; Customization
---

### Post by krumble on 2007-11-20
I am currently running gutsy and I had compiz working just fine with the effects and everything until earlier today.  I wanted to put in my ATI graphics card but it didn't work for some reason.  I am back to using the integrated Intel 915 card and had a little trouble getting the screen resolution back to where I wanted. After about an hour of messing around with the resolution I finally figured it out but I can't seem to get the desktop effects to work.  When I try to enable them I get an error message that says "Desktop effects could not be enabled".  Any help is greatly appreciated.

---

### Post by Forlong on 2007-11-20
First of all: are you really still on Edgy?

Then post the output of ```
compiz
``` in a terminal.


P.S. when adding a graphics card, you should always reconfigure the X-server:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by David RN on 2007-11-20
You might take a look at this post:
[http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+fresh+install+gutsy]("http://ubuntuforums.org/showthread.php?t=569654&highlight=ati+fresh+install+gutsy")

---

### Post by krumble on 2007-11-20
I had edgy and xp on my 80 gig hd but it filled up so I got a 250gig and did a fresh in stall of gutsy on it.

```
phantomfreak@phantomfreak:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

I don't want to try to put the graphics card in because when I did, Ubuntu would freeze on the load up and the only way to get it working again was to restart and go back to the integrated card

---

### Post by Forlong on 2007-11-20
Try running Compiz like this:
```
SKIP_CHECKS=yes compiz
```

---

### Post by krumble on 2007-11-20
This is what I get...

```
phantomfreak@phantomfreak:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by Forlong on 2007-11-20
Maybe you should post your xorg.conf - I'm somewhat confused as to what graphics card & driver you are using right now. You can use this command:
```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by krumble on 2007-11-21
Oh sorry, I didn't mean to confuse anyone. I just put some info about what happen incase anyone has any idea that I might have messed up a setting or something.  I am currently using the integrated intel 915 graphics.  I took the radeon x1300 completely out so there is no need to worry about that anymore.

```
phantomfreak@phantomfreak:~$ grep -v ^# /etc/X11/xorg.conf
Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "dri"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "Intel 915"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  0
        Vendorname      "Intel"
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1280x1024"
        Horizsync       31.5-64.0
        Vertrefresh     56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1280x1024@60"  "1280x960@60"   "1024x768@60"  "800x600@60"     "800x600@56"    "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by krumble on 2007-11-22
I just remembered that when I removed the graphics card (radeon x1300) and I restarted it using the integrated card that after it loaded the screen went black and it said running in low graphics mode.  I'm not sure if that could be a problem or not, but if any of you have any ideas on how to get the basic desktop effects working for me then I would love you forever =P

---

### Post by Forlong on 2007-11-22
Yeah, you're running in failsafe mode.
Here's how you "reset" your xorg.conf:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by krumble on 2007-11-22
I ran it and configured it as to what I think is correct so far, but it still doesn't work.  Any idea why that is? Also I'm not too sure if I configured everything correctly

```
phantomfreak@phantomfreak:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "altwin:meta_win"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
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
        Identifier      "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "SyncMaster 931B"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller"
        Monitor         "SyncMaster 931B"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

EndSection

```

---

### Post by Forlong on 2007-11-22
What's the output of ```
compiz
``` in a terminal?

---

### Post by krumble on 2007-11-22
```
phantomfreak@phantomfreak:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
```

---

### Post by krumble on 2007-11-22
I think the problem might be from the "texture_from_pixmap" what ever that is

---

### Post by Forlong on 2007-11-23
Check out [this page](http://wiki.compiz-fusion.org/Intel_with_AiGLX) to make sure your xorg.conf is set up correctly.

You have to restart X afterwards to check if it worked. Hope it helps.

---

### Post by krumble on 2007-11-23
Nope, I'm still getting the same problem

---

### Post by krumble on 2007-11-24
OK Solved it apparently I was still trying to run the ATI drivers or something like that. I saw in another post a person had a similar problem so he ran this command and it solved it.

```
sudo apt-get remove xorg-driver-fglrx
```

Thanks forlong for trying to help, hopefully you can help someone else next time with a similar problem

---

### Post by whirl on 2007-11-24
Hello!

Im new with this and to be honest I havent understand much of these different guides here so I was hoping if maybe somebody might help me get this working? 

I just did a clean sweep to 7.10 and when I tried to get this notorious compiz to work guess what? Didnt work. It pops a windows saying "Desktop effects could not be enabled"

Ill add every bit info Ive seen others pasting around if that might help you guys :)


```
whirl@spinning:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

whirl@spinning:~$ 
```

```
whirl@spinning:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting gtk-window-decorator
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

```
whirl@spinning:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
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
        Identifier      "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

        InputDevice     "Synaptics Touchpad"
EndSection
whirl@spinning:~$ 

```

So anyone out there who could guide through this? Id love to get this working but I really dont have idea where to start.

Cheers!

---

### Post by Forlong on 2007-11-25
See the link I posted above, you're missing some modules. The weird thing is, you don't even have a *Section "Module"*

---

### Post by whirl on 2007-11-25
Yub I noticed it too and so decided that I have been doing something silly. Anyone with intel chipset and has compiz working? Maybe post your xorg so I could try to match these things? Like where is that module suppose to be and what else am I missing. This is quite weird maybe the install didnt go that well?

Cheers!

---

### Post by krumble on 2007-11-25
I dont have a section module either.....I have mine working now though.

---

### Post by krumble on 2007-11-25
Whirl type this in the terminal and post what it says

```
glxinfo | grep direct
```

---

### Post by whirl on 2007-11-26
```
whirl@spinning:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

That is what it gave me this time. I dont know what happened but something did happen. Ive been searching for guides on this matter and have been doing some experimenting. It seems its working. I have cube, wobbly windows and all. Umm okies. Cheers for everyone for your help but it seems its working now. Ill write here if I run to any problems in the near future (with my luck tomorrow)

---

