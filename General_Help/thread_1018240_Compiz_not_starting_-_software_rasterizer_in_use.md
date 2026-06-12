---
title: "Compiz not starting - software rasterizer in use"
date: 2008-12-21
forum: General Help
---

### Post by acablue on 2008-12-21
I connected my PC to my TV with a VGA connection to play a movie, and now I cannot enable any desktop effects, regardless of whether I use the default window manager or Compiz. I downloaded the Compiz-check script to diagnose the problem and here is the output:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```

---

### Post by acablue on 2008-12-21
Oh and I should add:

```
alex@alex-laptop:~/Downloads$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 


```

---

### Post by shakaran on 2008-12-22
Maybe this thread is related (same sympthons):
[http://ubuntuforums.org/showthread.php?p=6416499](http://ubuntuforums.org/showthread.php?p=6416499)

---

### Post by gimartinez on 2009-01-09
I found a solution for this in the following link:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/270122](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/270122)

The issue is being generated when you connect an external monitor,  the configuration file will change your resolution affecting the rasterizer software. Some controller boards like mine Intel Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller, can't operate with resolution bigger than 2048

I changed my /etc/X11/xorg.conf file in the display section

you can change it using the following command:
sudo nano /etc/X11/xorg.conf

This is the section that i changed:

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 1050
# Virtual 2960 1050

	EndSubSection
EndSection

Hopefully you can fix it.

:popcorn:

---

### Post by gumbl on 2009-04-11
Hi I'm havin' the same problem. But... I do not want to restrict the resolution to 648 on my widescreen. My Native resolution that fits my screen is 1980x1050 and on the laptop it is 1400x1050 (it's an nc6320 hp laptop)

I'm using the Intel driver and do not seem to get the gfxcard to work.
is there a way to get compiz to work without using a crappy resolution like 648x1050 on an 1980x1050 screen with the hardware included in this type of laptop? or is there a restriction due to card capabilities? or is it the driver itself that isn't well enough written...

Note* When I'm dualbooting to my winxp installation of the same machine I can run at least 1400x1050 + 1280x1024 wich is ok as well. I do not need tha full res on my external screen, although it would be nice...

Think I have browsed around for several sites to find a sollution to my problem bur I haven't found any... yet.


output from lspci

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

my xorg file

> 
Section "Monitor"
	Identifier	"DFP-1"
	Option		"DPMS"
	HorizSync 30-86
	VertRefresh 50-180
	Modeline "1400x1050_75.00" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"DFP-1"
	Device		"Device 1"
	SubSection "Display"
		Virtual	3080 1050
	EndSubSection
EndSection

Section "Module"
	Load "glx"
	Load "GLcore"
	Load "dri"
	Load "v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Device"
	Identifier      "Device 1"
	Driver "intel"
	BusID "PCI:0:2:0"
	Option "TwinView"	"False"
	Option "XAANoOffscreenPixmaps" "true"
	Option "AllowGLXWithComposite" "true"
	Option "AddARGBGLXVisuals" "true"
	Option "DisableGLXRootClipping" "true"
	Option "AIGLX" "On"
	Option "DRI" "true"
EndSection

ps... the xorgfile is rather much genereated via the monitor section under system -> configuration -> resolutions... and not manually written.
so It's not customized in any way.

Have earlier on tried to get xinerama to do everything for me.. but it didn't work out in a acceptable manner. 

If you have any Ideas I will be pleased to hear them!

Tune out.

---

### Post by thefluxster on 2009-06-23
> **gumbl said:**
> Hi I'm havin' the same problem. But... I do not want to restrict the resolution to 648 on my widescreen. My Native resolution that fits my screen is 1980x1050 and on the laptop it is 1400x1050 (it's an nc6320 hp laptop)

I'm using the Intel driver and do not seem to get the gfxcard to work.
is there a way to get compiz to work without using a crappy resolution like 648x1050 on an 1980x1050 screen with the hardware included in this type of laptop? or is there a restriction due to card capabilities? or is it the driver itself that isn't well enough written...

Note* When I'm dualbooting to my winxp installation of the same machine I can run at least 1400x1050 + 1280x1024 wich is ok as well. I do not need tha full res on my external screen, although it would be nice...

Think I have browsed around for several sites to find a sollution to my problem bur I haven't found any... yet.


output from lspci



my xorg file



ps... the xorgfile is rather much genereated via the monitor section under system -> configuration -> resolutions... and not manually written.
so It's not customized in any way.

Have earlier on tried to get xinerama to do everything for me.. but it didn't work out in a acceptable manner. 

If you have any Ideas I will be pleased to hear them!

Tune out.


I have the same issue here - two 20" 1600x1200 monitors.  I can set the virtual desktop to render on both of them, but I lose Compiz and therefore some really nice features of Ubuntu in the processs.  :(

If anyone has any insight, it would be most appreciated.
 Hardware:              Dell Latitude D430
 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

---

### Post by wladek on 2009-08-04
Guys, I have the same problem. You should download the external program called compiz-check on [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch) ,if you run it you should see what is your problem. I have hp nc6320 and using Intel driver. Some months ago I run this command and it told me that my graphic card do not show more than 2048 resolution. So if you running notebook monitor and external monitor you will be not able to get the full size resolution from it. But now I have much bigger problem. I disconnected the external monitor and restart ubuntu, but compiz do not want to start again. I ran the compiz-check script, but it cannot help me. Please, help me guys, or I'm switching back to Windows after 2 years :-P :-D

---

### Post by wladek on 2009-08-04
Ok, guys I found solution, thanks to _gimartinez_ , if you open 

/etc/X11/xorg.conf

you need to change the line which says: Virtual
for example, my resolution is 1400x1050 and I had "Virtual 2790 1050"

you need to change it to
"Virtual 1400 1050"

And done :) 
Hope you solve your problems...

And one question for advanced people. Could avant windows navigator runs without windows effects? It would be great :) I'm doing it only because I'm using AWN :)

---

### Post by theonlygunk on 2009-08-06
[I][B]Ok, guys I found solution, thanks to _gimartinez_ , if you open 

/etc/X11/xorg.conf

you need to change the line which says: Virtual
for example, my resolution is 1400x1050 and I had "Virtual 2790 1050"

you need to change it to
"Virtual 1400 1050"

[/B][/I]I tried this and I get:
/etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied

I am new to UBUNTU and I have no idea what I am doing, its dark here, and people are I hear laughing!

I run compiz check and I get the fail: software rast in use... help me please

theonlygunk

---

### Post by Ruelyo on 2009-08-06
> **theonlygunk said:**
> [I][B]Ok, guys I found solution, thanks to _gimartinez_ , if you open 

/etc/X11/xorg.conf

you need to change the line which says: Virtual
for example, my resolution is 1400x1050 and I had "Virtual 2790 1050"

you need to change it to
"Virtual 1400 1050"

[/B][/I]I tried this and I get:
/etc/X11/xorg.conf
bash: /etc/X11/xorg.conf: Permission denied

I am new to UBUNTU and I have no idea what I am doing, its dark here, and people are I hear laughing!

I run compiz check and I get the fail: software rast in use... help me please

theonlygunk



sudo nano /etc/X11/xorg.conf

---

### Post by AROtotheN on 2009-09-22
Cheers, worked for me.

---

### Post by gksudo on 2009-09-22
I had a similar problem.

---

### Post by NGKEIB on 2009-10-11
Hi, my long searches for a solution to this have led me here...

Unfortunately the suggestion from above (changing the Virtual Resolution in /etc/X11/xorg.conf) did not work for me - I still get the 'could not be enabled' when I try to change from 'None' to 'Normal' in Appearances.

Any ideas?  I can provide information if required.

Thank you in advance.

---

### Post by NGKEIB on 2009-10-11
How curious - I looked at the advice listed here ([http://ubuntuforums.org/showthread.php?t=1030154&page=3](http://ubuntuforums.org/showthread.php?t=1030154&page=3)), and went to gconf-editor etc., but noticed that instead of being checked so that I could uncheck it, the compositing manager box was in fact unticked.  So I ticked it, and all of a sudden my avant-window-navigator popped up, so it looked as if things are back to normal.  However, I can still not enable any effects...

---

### Post by LoseTheGame on 2009-10-14
I'm quite new to the Linux Community but I found something that worked for me when Compiz wouldn't start. I had the same errors: "Desktop effects could not be enabled" and "Software rasterizer in use" when I ran Compiz-Check. Hope this helps:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by alturion on 2009-10-27
I have the same problem...
From the moment that i connect my external monitor trought the VGA connector, I cant use compiz or the default metacity (i.e. the wheel mouse doest switch anymore the workspaces).


lspci | grep VGA 
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

```glxinfo | grep rendering
```
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
```compiz --replace &
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity 

```This is the compiz-check answer:
```

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use 

```This is my xorg.conf:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display"
#        Virtual 800 600
        Virtual    2304 1024
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
        Option          "EXAOptimizeMigration"          "true"    
        Option          "MigrationHeuristic"            "greedy" 
        Option          "Tiling"                        "false" 
EndSection

```I have tried to change the Virtual but for any value I put in it I cannot start again the X-server.

Thank you

---

### Post by alturion on 2009-10-29
Solved!

I solved all the problems with my graphic card installing the new drivers and reconfiguring:
```

sudo nvidia-settings --uninstall
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg 
```
[URL="http://ubuntuforums.org/showthread.php?t=1301433&highlight=driver+i915"]
http://ubuntuforums.org/showthread.php?t=1301433&highlight=driver+i915[/URL]

---

### Post by crazy2be on 2009-11-03
If none of the above solved your problem, I found that when the updator crashed, it did everything except change my kernel. So, I was booting the 9.04 kernel with the 9.10 software... Didn't work so well. Anyway, do a 
sudo gedit /boot/grub/menu.lst
And change the first entry to your newest kernel. You can find this out by typing
ls /boot
Hope that helps someone! Great job on 9.10, although the updater team really needs to get it's act together. Had I not known what I did, this would of been several days of frustration. As it was, it was a night with very little time to sleep ;).

---

### Post by boilertnerb on 2009-12-04
changing my xorg to "Virtual 1900 1050" worked for me as well... running macbook 1,1. 

was looking for this one for awhile, thanks for the help!

---

### Post by johnnybob on 2009-12-14
My compositioning works fine but when i ran the test it shows that software rasterization and Xgl is not present but i attached my Xorg.0.log that says it was loaded wtf?

why?

johnnybob@smackdaddy:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1152x864) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

---

