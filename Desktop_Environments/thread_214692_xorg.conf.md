---
title: "xorg.conf"
date: 2006-07-12
forum: Desktop Environments
---

### Post by mumebuhi on 2006-07-12
My current setting (Screen Resolution Preferences):
Resolution: 1400x1050
Refresh Rate: -15072 Hz

Why would the Refresh Rate a negative number?

Also, there is no other option for the Resolution. I added "1280x1024" to the following line in /etc/X11/xorg.conf file
---start---
SubSection "Display"
  Depth           24
  Modes           "1400x1050" "1280x1024"
EndSubSection
---end---
However, the system still does not pick the newly-added option. Help?

Thank you.


Buhi

---

### Post by orb9220 on 2006-07-13
Refresh Rate: -15072 Hz

should be like

Refresh Rate: 50-72 Hz

Maybe ? Mine is

Option		"SecondMonitorHorizSync" "30-70"
Option		"SecondMonitorVertRefresh" "60"

Also post your vedeo card type then people can give more help
Hope this helps.

---

### Post by Dr. Nick on 2006-07-13
look in my signature, I have a little basic tutorial about refresh problems I made, Your refresh looks wrong, that is probably causing the resolution problem. You can either find out your correct refresh, or just reconfigure X

---

### Post by mumebuhi on 2006-07-13
I actually have a 17" Dell E171FP monitor hooked up to my old Sony laptop, PCG-GR390. Currently, the display on the laptop works OK, that is using the maximum resolution 1400x1050. However, the display is not OK on the monitor--obviously because the monitor only supports max resolution of 1280x1024.

I am a newbie regarding X. For example, where to find information about my video card? Is this the one?
---start---
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection
---end---

What other information do I need to provide in order to help others to help me?

---

### Post by mumebuhi on 2006-07-13
This is my xorg.conf file.

---start---
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
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
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        ModelName       "Dell E171FP"
        HorizSync       30-80
        VertRefresh     56-76
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050" "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050" "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050" "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050" "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050" "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x1024"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection
---end---

---

### Post by Dr. Nick on 2006-07-13
Are you trying to get the monitor hooked up to the laptop at 1280x1024? If so then the way you have it looks correct. If it choosing the 1400x1050 on you and you can not read the screen then, you can remove the 1400x1050 lines and it will force it down to 1280x1024 since that it all that is left.


That will however mess up the laptop display when you use it, you would have to add the 1400x1050 back in. Is the 1400x1050 readable on the external monitor? if it is readable then I would leave it like you have it and just use the System- Preferences -Scree Resolution option to switch between

---

### Post by mumebuhi on 2006-07-13
Dr. Nick,

You are right! Deleting the "1400x1050" from the lines actually forces the system to pick up the only configuration left, that is 1280x1024. Thank you, this helps. Luckily, this does not mess up the laptop display. Now, both the displays on my laptop and monitor use 1280x1024. 

However, two things I still don't understand:
1. Before I made the change (as in the complete xorg.conf posted in the previous reply), System-Preferences-Screen Resolution only detects 1400x1050 (although there is another option, 1280x1024). Why is that?
2. The Refresh Rate is still negative.

Help?

Thank you.


Buhi

---

### Post by Dr. Nick on 2006-07-13
Weird, not sure why it wouldnt display all options, maybe its realted to the refresh or something. What does the refresh rate say in the Sys-Prefs-ScrnRes section? I do not see where the refresh is negative in your last post with the full xorg.conf, I see a positive one

        HorizSync       30-80
        VertRefresh     56-76


I havent done much with multiple outputs so I am not totally sure how it is all supposed to work.

---

### Post by mumebuhi on 2006-07-13
Hhmm... with the posted xorg.conf, I still get the following :(
Refresh Rate: -15072 Hz

---

### Post by Dr. Nick on 2006-07-13
Thats weird, Dont know how you could fix that, maybe reconfiguring X using 

sudo dpkg-reconfigure xserver-xorg

would solve it, I have a few tips posted in my first signature link on doing that, If you do this though I would backup your current xorg.conf just incase it makes matters worse

---

### Post by bennis on 2008-05-22
My problem is not that i have a low resolution, my problem is that i have no 3D effects. I can't even play Bubble Trouble or whatever that game is. I think this is due to not having any drivers for my video card, but i don't know. I also don't know how to check to see if i have drivers for this. Any ideas?

---

