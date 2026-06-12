---
title: "Change login screen resolution?"
date: 2006-03-27
forum: Desktop Environments
---

### Post by kcy29581 on 2006-03-27
Hi all,

When Ubuntu boots up and loads Xorg, the first screen you see is the login screen.

The resolution has been set higher than I prefer. To make things clear, my monitor has been 100% detected, and Ubuntu has set my default resolution to the highest possible for my monitor, 1280x1024. I would rather have it at 1024x768.

I have set the resolution to 1024x768 in the desktop, using System -> Preferences -> Screen Resolution. All is fine there! But this makes no difference to the login screen resolution.

I have found a way to deal with this: If I remove all references to 1280x1024 in /etc/X11/xorg.conf (in the Screen section -> Modes) then it defaults to the next highest resolution, 1024x768. But when I do this I feel like I'm crippling my monitors abilities, say if a game ever needed the highest resolution. So I'm looking for a cleaner (gui?) way of dealing with this.

Any help or advice would be appreciated!

---

### Post by ticlo on 2006-03-27
In /etc/X11/xorg.conf, the first entry in the "modes" lines of the various Screen->Display subsections determines the default resolution for X.

So, for instance, if this is the Screen section in my xorg.conf file, the default resolution will be 1024x768:
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"17P3"
	DefaultDepth	24

	[...]

	SubSection "Display"
		Depth		24
		Modes		"1024x768" "1280x960" "640x480" "800x600"
	EndSubSection
EndSection
```
The higher 1280x960 resolution is still available.

Hope that helps :)

---

### Post by Leigh on 2006-03-27
Thanks, that certainly helped me as I was having the same issue.

---

### Post by kcy29581 on 2006-04-01
Thanks alot ticlo! :)

---

### Post by LantagoniE on 2006-12-20
it didn't work for me.  i put "1280x1024" first on all the Display sub sections i have in my xorg.conf file.  I even tried to completely remove the "1600x1200" resolutions within the sub sections but the resolution during the startup screen and the login screen are still to big for my monitor.  Any ideas?

---

### Post by mcduck on 2006-12-20
I always do that with the simple way, in Gnome's resolution settings choose the resolution you want and then mark the 'make default for this computer'-box.

---

### Post by Nader43 on 2007-02-09
im having the same problem, im new to Ubuntu i dont know how to get to /etc/X11/xorg.conf what do i type in terminal to get there. and when there how do i change the login screen res down to 1280x1024

---

### Post by shareMenaPeace on 2007-02-10
> **Nader43 said:**
> im having the same problem, im new to Ubuntu i dont know how to get to /etc/X11/xorg.conf what do i type in terminal to get there. and when there how do i change the login screen res down to 1280x1024

backup before you edit it with

[HTML]cp /etc/X11/xorg.conf /home/<Your Username>/Desktop[/HTML]

edit with

```
gksudo gedit /etc/X11/xorg.conf
```

note in linux all is case sensitive

Once open scroll down to the bottom but make sure your screen supports thie resolution.
If you do something wrong, np you have a backup than.

---

### Post by maxwellcom on 2007-02-13
> it didn't work for me. i put "1280x1024" first on all the Display sub sections i have in my xorg.conf file. I even tried to completely remove the "1600x1200" resolutions within the sub sections but the resolution during the startup screen and the login screen are still to big for my monitor. Any ideas?

LantagoniE, you might be editing the wrong section of xorg.conf, as I was.  Found a solution here:

[http://ubuntuforums.org/showthread.php?t=359310]("http://ubuntuforums.org/showthread.php?t=359310") 

hope that helps

---

### Post by Gallo_Pinto on 2007-12-27
Thanks Ticlo! An easy fix for a really annoying problem. Worked great!

---

### Post by simonfiction on 2007-12-29
> **mcduck said:**
> I always do that with the simple way, in Gnome's resolution settings choose the resolution you want and then mark the 'make default for this computer'-box.

I've been having the same problem and just to let people reading this know that this option doesn't work for me. I'm guessing other people have had the same problem. The check box does absolutely nothing, it doesn't affect anything. I'm guessing this must be a bug?

-Si

---

### Post by simonfiction on 2007-12-29
Also, just went into my xorg.conf to try and apply the suggested fix but the correct resolution is already set as the first mode - 1680 x 1050. Here's the screen section of my xorg...

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"DELL E207WFP"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1680x1050@60"	"1680x1050@75"	"1600x1024@60"	"1920x1200@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection

```

Is there anywhere else that the login screen would reference the screen resolution?

Thanks,
Si

---

### Post by TeaSwigger on 2007-12-30
Hello,

Have a look at the part in the xorg you posted where it says "Virtual." Backup the file (as always) and then try changing the "Virtual" entry to the desired screen size, so that if you desire 1680 x 1050 the line should specify:

```
Virtual    1680 1050
```

...and give that a go. :)

---

### Post by erginemr on 2008-01-02
I am also suspecting the "Virtual" line. If the above tip does not work, try to comment it out with:
```
#      Virtual	1920	1200
```

---

### Post by observative on 2008-01-05
Hi, I don't know if you solved the login screen resolution? But as I was trying to get several monitor screen issues solved, including this one, I came across these threads and thought they might help you solve it.

This one delt with the xorg.conf file and the virtual settings:
[http://ubuntuforums.org/showthread.php?t=359310](http://ubuntuforums.org/showthread.php?t=359310)

This one deals with the Configuration Editor and a key setting for Login Screen: [http://ubuntuforums.org/showthread.php?t=47601](http://ubuntuforums.org/showthread.php?t=47601)

Hope it helps

---

### Post by ThunderVamp9 on 2008-06-25
Nm

---

### Post by Mad_Max_1412 on 2008-07-08
Guys,

I have 2 computers and I use a single monitor/mouse/keyboard via the use of a KVM switch.

If I have the KVM switch set to the Ubuntu box when I boot it up (whether the monitor is on or not) it comes up in the correct resolution of 1680x1050.

Unfortunately if the KVM switch is set to the other computer when I'm booting the Ubuntu box, my screen is set to something like 800*600 and everything is so big and cramped that I can't select the "System" pull down menu to manually change the resolution (it picks up on the Swiftweasel icon that's in the same area).

The only thing I can do is to reboot and wait until comes back up before switching back to my second computer.

I've looked through the forums and changed my conf file so that 1680x1050 was the first thing for each of the modes and tested it but no luck.

Here's my conf file.
> 
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "dbe"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "record"
    Load           "v4l"
    Load           "vbe"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "au"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer AL2216W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
EndSection

Section "Device"
    Identifier     "Nvidia GeForce 6600"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Nvidia GeForce 6600"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050 +0+0; 800x600 +0+0; 640x480 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


Any suggestions?  It's annoying that I can't boot up the Ubuntu box whilst I'm working on the 2nd computer.

---

