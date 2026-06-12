---
title: "X Config for Dells with Intel Graphics"
date: 2007-11-19
forum: Dell  Ubuntu Support
---

### Post by sciurus on 2007-11-19
I've seen a lot of threads in this forum from people having trouble configuring X for multiple displays on Intel graphics hardware. Unfortunately, Ubuntu's Screens and Graphics tools[ doesn't handle this right]("https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/125941").

Below is a configuration that has been tested on my 1420N. As you can see, not a lot of manaul configuration is required. I expect this to work on any system with Intel graphics hardware.

The line you may want to edit is *Virtual 3200    1880*. This controls the largest display area you will be able to use. With these numbers, I am able to have either a horizontal or vertical arrangement with my WXGA internal display and a WUXGA external display.

```

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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 3200    1880
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen          "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

```

How do you actually use multiple monitors? The easy answer is the GUI configuration tool grandr. Unfortuantely, this [seems broken in Gutsy]("https://bugs.launchpad.net/debian/+source/grandr/+bug/127829"). The alternative is the xrandr utility. For details on it you can read the man page. Here are a few examples:

xrandr --output VGA --auto --right-of LVDS
xrandr --output VGA --off

---

### Post by sciurus on 2007-11-19
Another common problem is the inability to use Compiz on G965 / X3000 video. [Ubuntu doesn't make this very clear]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/152226"), but this is disabled for a reason- it breaks video playback using XV. However, XV is by no means a requirement for playing videos. Here are two steps for enabling compiz:

[LIST=1]
[*]run gstreamer-properties and change the video output to 'no xv'
[*]run the following command *mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager*
[/LIST]

Now you can start desktop effects from the appearance capplet. If you do have problems, just disable compiz. Don't expect any support.

---

### Post by 244f on 2007-11-20
i have an x3100 and i'm running gutsy. i have no problem with an external monitor, i just plug it and reboot and it automatically clones.. but i don't know how to use an extended desktop option since its greyed out in the graphics options. will your method enable that ?

---

### Post by sciurus on 2007-11-20
> **244f said:**
> i have an x3100 and i'm running gutsy. i have no problem with an external monitor, i just plug it and reboot and it automatically clones.. but i don't know how to use an extended desktop option since its greyed out in the graphics options. will your method enable that ?

Yes, this method allows cloning and extending, plus you won't need to reboot.

---

### Post by sciurus on 2007-11-22
There are guides to using xrandr at [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) and [http://www.phoronix.com/scan.php?page=article&item=927&num=1](http://www.phoronix.com/scan.php?page=article&item=927&num=1). There is a thread with an explanation of the xorg.conf file as well as a script o configure your monitors on login [here]("http://ubuntuforums.org/showthread.php?t=581947").

---

### Post by Innomatics on 2007-12-06
Thanks this also works perfectly with a Zepto 3215W (Compal IFL91) and an external 1280x1024 LCD panel

---

### Post by visionofarun on 2007-12-06
Scirus,

I tried the given for compiz, but it did not work. I am on G965/X3100 Video. Any help?
However, I did not try the external videos.

---

### Post by dvwyngaa on 2007-12-11
> **sciurus said:**
> I've seen a lot of threads in this forum from people having trouble configuring X for multiple displays on Intel graphics hardware. Unfortunately, Ubuntu's Screens and Graphics tools[ doesn't handle this right]("https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/125941").

Below is a configuration that has been tested on my 1420N. As you can see, not a lot of manaul configuration is required. I expect this to work on any system with Intel graphics hardware.

The line you may want to edit is *Virtual 3200    1880*. This controls the largest display area you will be able to use. With these numbers, I am able to have either a horizontal or vertical arrangement with my WXGA internal display and a WUXGA external display.

```

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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 3200    1880
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen          "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

```

How do you actually use multiple monitors? The easy answer is the GUI configuration tool grandr. Unfortuantely, this [seems broken in Gutsy]("https://bugs.launchpad.net/debian/+source/grandr/+bug/127829"). The alternative is the xrandr utility. For details on it you can read the man page. Here are a few examples:

xrandr --output VGA --auto --right-of LVDS
xrandr --output VGA --off

sciurus,

I have tried your config with my hardware and it just doesn't wanna work. I have a HP6710b notebook with Gutsy loaded. Natively the screen supports 1680x1050 and an External Dell LCD screen taht support 1280x1024. The native graphics card is an Intel X3100. With the mentioned config, and anything else I have tried, once I boot I get my LCD popping up as the primary screen and my other screens secondary screen option in the Xorg.conf tool, greyed out.

I also see two "Screen 1" options! When I do boot up with the external screen connected, the primary screen has a res of 800x600 and it not "seperate" screen, but your normal cloned screen which, needless to say, I don't want. I would like to have dual screen or have two seperate screen where I can work on the one screen with coding and work on the other screen reading say a help file.

Any suggestions / help would be most welcome...

Dawid

---

### Post by sciurus on 2007-12-11
> **dvwyngaa said:**
> sciurus,

I have tried your config with my hardware and it just doesn't wanna work. I have a HP6710b notebook with Gutsy loaded. Natively the screen supports 1680x1050 and an External Dell LCD screen taht support 1280x1024. The native graphics card is an Intel X3100. With the mentioned config, and anything else I have tried, once I boot I get my LCD popping up as the primary screen and my other screens secondary screen option in the Xorg.conf tool, greyed out.

I also see two "Screen 1" options! When I do boot up with the external screen connected, the primary screen has a res of 800x600 and it not "seperate" screen, but your normal cloned screen which, needless to say, I don't want. I would like to have dual screen or have two seperate screen where I can work on the one screen with coding and work on the other screen reading say a help file.

Any suggestions / help would be most welcome...

Dawid

Don't use the xorg.conf tool; you need to use xrandr instead. When you boot with this X configuration and your external LCD screen connected, what does ```
xrandr -q
``` show?

---

### Post by sciurus on 2007-12-11
> **visionofarun said:**
> Scirus,

I tried the given for compiz, but it did not work. I am on G965/X3100 Video. Any help?

Can you provide more information on what didn't work and how you know this?

---

### Post by visionofarun on 2007-12-11
> **sciurus said:**
> Another common problem is the inability to use Compiz on G965 / X3000 video. [Ubuntu doesn't make this very clear]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/152226"), but this is disabled for a reason- it breaks video playback using XV. However, XV is by no means a requirement for playing videos. Here are two steps for enabling compiz:

[LIST=1]
[*]run gstreamer-properties and change the video output to 'no xv'
[*]run the following command *mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager*
[/LIST]

Now you can start desktop effects from the appearance capplet. If you do have problems, just disable compiz. Don't expect any support.

I tried enabling the desktop effects but it showed "Desktop effects could not be enabled"
This is what i get when i run compiz from a terminal:
> arun@AUM:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

---

### Post by sciurus on 2007-12-12
> **visionofarun said:**
> I tried enabling the desktop effects but it showed "Desktop effects could not be enabled"
This is what i get when i run compiz from a terminal:

You're using ATI graphics, not Intel. I can't help you.

---

### Post by dvwyngaa on 2007-12-20
> **sciurus said:**
> Don't use the xorg.conf tool; you need to use xrandr instead. When you boot with this X configuration and your external LCD screen connected, what does ```
xrandr -q
``` show?

The output for xrandr -q is as follows:

Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 3200 x 1880
VGA connected 1280x1024+1280+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
LVDS connected 1280x800+0+0 (normal left inverted right) 331mm x 207mm
   1680x1050      60.6 +
   1280x800       60.0* 
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right)


I got the dual monitor working now, but my notebook screen is running 1280x800 and its capable of 1680x1050 and is seen as the secondary screen, not the primary.

Here is the output of my xorg.conf:

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 3200    1880
        EndSubSection
EndSection

Any help will be appreciated...

Thanks,

Dawid

---

### Post by kuja on 2007-12-20
blackwaltz@spira:~$ xrandr --output TV --auto --right-of LVDS
xrandr: screen cannot be larger than 1440x1440 (desired size 2464x900)


How would one go about fixing this?

---

### Post by hyperandy on 2008-03-18
> **sciurus said:**
> Another common problem is the inability to use Compiz on G965 / X3000 video. [Ubuntu doesn't make this very clear]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/152226"), but this is disabled for a reason- it breaks video playback using XV. However, XV is by no means a requirement for playing videos. Here are two steps for enabling compiz:

[LIST=1]
[*]run gstreamer-properties and change the video output to 'no xv'
[*]run the following command *mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager*
[/LIST]

Now you can start desktop effects from the appearance capplet. If you do have problems, just disable compiz. Don't expect any support.


This works great on the Acer 4720Z Laptop with one exception. 
You can have Compiz but you cannot view the built in webcam with 'no vx' enabled at a normal framerate.
To be more specific, with 'no vx' selected the camera is very slow and with 'X Windows System' enabled the camera responds normally. 
As a note, I have not tried it with skype. However, running cheese and recording a video worked fine even though what I was seeing was slow - it did recorded in real time. 

So to sum it up... with 'no vx' camera=slow but evidently working properly

and with 'X Windows System' camera responds great both ways but you have no pretty 3D compiz. 

If anyone knows a work around or anything please post it!

---

### Post by Thelasko on 2008-04-07
[Vote it up on brainstorm!]("http://brainstorm.ubuntu.com/idea/4537/")  We need that driver fixed.[IMG]http://brainstorm.ubuntu.com/idea/4537/image/1/[/IMG]

---

