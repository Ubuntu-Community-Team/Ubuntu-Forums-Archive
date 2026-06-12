---
title: "XGL/compiz or beryl on intel GMA 950?"
date: 2006-12-08
forum: Desktop Environments
---

### Post by lwtinman17 on 2006-12-08
Can anyone give me or point me to a tutorial on how to setup either xgl/compiz or xgl/beryl on a intel GMA 950 graphics card... any help would be appreciated.

---

### Post by endersshadow on 2006-12-08
[http://wiki.beryl-project.org/wiki/Install/Ubuntu](http://wiki.beryl-project.org/wiki/Install/Ubuntu)

Follow directions for AIGLX for your version of Ubuntu (Dapper or Edgy).  Since you use an Intel GPU, you need AIGLX.

---

### Post by lwtinman17 on 2006-12-08
Thanks, exactly what i was lookin for

---

### Post by encompass on 2006-12-15
Well did it work?  I am looking to buy a computer with the 950 and will go for the 945 if it doesn't work.  So it would be nice to know if you had big problems.

---

### Post by apakun on 2007-01-05
My computer has Intel GMA 950 card. But after following the instruction for AIGLX in [http://wiki.beryl-project.org/wiki/Install/Ubuntu](http://wiki.beryl-project.org/wiki/Install/Ubuntu), every thing is broken (black screen after restarting) so I have to return to the default configuration.

Is that correct direction for my graphic card? What should I do for using Beryl now?

---

### Post by encompass on 2007-01-05
I don't doubt that it would work.  I purchased my laptop with the intel chipset and it seems to work just fine.  I like it ALOT.  And it works in beryl.  I followed your same link too.  MAke sure you did it right.

---

### Post by apakun on 2007-01-05
One of my problem is

% sudo apt-get install linux-dri-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-dri-modules-2.6.17-10-generic

Is this the reason? How can I solve this?

Thanks a lot

---

### Post by encompass on 2007-01-05
> **apakun said:**
> One of my problem is

% sudo apt-get install linux-dri-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-dri-modules-2.6.17-10-generic

Is this the reason? How can I solve this?

Thanks a lot
are you sure it didn't say...
sudo apt-get install linux-restricted-modules-`uname -r`-generic
or in your case... this should work too...
sudo apt-get install linux-restricted-modules-2.6.17-10-generic
For some reason that link is down today...
but yeah... that should get it running...
if you still can't find that package... then make sure you have all repositories turned on.

---

### Post by apakun on 2007-01-05
that package is already installed in my machine.

I try modifying my /etc/X11/xorg.conf as the direction but having problem with the last step

Section "Extensions"
Option "Composite" "Enable"
EndSection

Also, I cannot add the below lines to my /etc/gdm/gdm.conf-custom

[server-aiglx]
name=aiglx server
command=/usr/bin/Xorg-air :0
flexible=true

---

### Post by encompass on 2007-01-05
You need to be root to make those changes happen.
Put sudo in front of the text editor name that your useing...
```
sudo gedit /place/of/file.conf
```
your progressing...

---

### Post by apakun on 2007-01-06
I didn't mean that I can't edit the file. I mean when I follow [http://wiki.beryl-project.org/wiki/Install/Ubuntu/Dapper/AiGLX#Install_AIGLX](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Dapper/AiGLX#Install_AIGLX),  step by step, the following part makes problem to my display

Section "Extensions"
Option "Composite" "Enable"
EndSection

And also the configuration of /etc/gdm/gdm.conf-custom

Please give me an advice, thanks.

---

### Post by encompass on 2007-01-06
Make sure you did all the steps... then tell me or better post the error that you get.  be a detailed as possible.  The intel chipset is probably the easiest to setup beryl with.  SO I HIGHLY doubt that it will not work.  But don't give up.  It will come soon enough.

---

### Post by apakun on 2007-01-07
Thanks for you encouragement, I am trying my best.

The error in my machine is when I restart gdm after adding the mentioned lines (to enable the composite mode in xorg.conf). My machine displays nothing, then I have to use Ctrl-Alt-F6 and restore the original xorg.conf. ](*,) 

Do you think it is because I have failed installing linux-dri-modules-`uname -r`
? (as mentioned before)

---

### Post by encompass on 2007-01-07
Tell me again... are you running dapper or edgy... version 6.06 or 6.10.  Both are good but I need to know to help a little more...
I am using similar instructions, but they are for edgy.

---

### Post by apakun on 2007-01-07
I think I have tried all of them, could you send me the instruction that you used? And your xorg.conf ?

---

### Post by encompass on 2007-01-08
Please answer my questions...  Then we can move further.
Or wait for feisty.

---

### Post by apakun on 2007-01-08
I follow edgy instruction.

I figure out that the display is hung when I run Beryl with Option "Composite" "Enable" in xorg.conf

---

### Post by encompass on 2007-01-08
run this...
```
glxinfo | grep render
```
and post your output...
you should get something like this...

OpenGL renderer string: Mesa DRI Intel(R) 945GM 20050225
encompass@essence:~$ glxinfo | grep render
libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20050225
encompass@essence:~$

---

### Post by apakun on 2007-01-08
Here it is:

apakun@apk:~$ glxinfo | grep render
direct rendering: No
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20050225

---

### Post by encompass on 2007-01-08
OK problem number one... you don't have Derict Redering... in otherwords... even if you have the Beryl working it would work so slow you couldn't stand it.
I think you had it just fine but perhaps lots it in the mess.
could you send me the out put of your xorg.conf file...
```
gedit nano /etc/X11/xorg.conf
```
Thanks....

---

### Post by encompass on 2007-01-08
Also... is this a desktop or mobile and do you have a widescreen?

---

### Post by apakun on 2007-01-08
Mine is a laptop with 12" screen. Here is the xorg.conf:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
	Load	"dbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"vn"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option "Composite" "On"
	Option "XAANoOffscreenPixmaps"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
	Option "AIGLX" "true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
  Option "Composite" "Enable"
EndSection

---

### Post by encompass on 2007-01-08
Try this....
Be sure to back things up...

Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/fonts/cyrillic"
FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi"
FontPath "/usr/share/fonts/X11/misc"
# path to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
Load "dbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "vn"
Option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "stylus"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "eraser"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/wacom" # Change to
# /dev/input/event
# for USB
Option "Type" "cursor"
Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "Device"
Identifier "Intel Corporation Mobile Integrated Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile Integrated Graphics Controller"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x800"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x800"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "stylus" "SendCoreEvents"
InputDevice "cursor" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
	Mode 0666
EndSection

---

### Post by encompass on 2007-01-08
Here is mine to show the difference....
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
Identifier      "Synaptics Touchpad"
Driver          "synaptics"
Option          "SendCoreEvents"        "true"
Option          "Device"                "/dev/psaux"
Option          "Protocol"              "auto-dev"

#Option          "LeftEdge"      "100"
#Option          "RightEdge"     "1120"
#Option          "TopEdge"       "50"
#Option          "BottomEdge"    "310"

#Option          "FingerLow"     "25"
#Option          "FingerHigh"    "30"

#Option          "MaxTapMove"    "220"

#Option          "TapButton1"    "1"
#Option          "TapButton2"    "3"
#Option          "TapButton3"    "2"

#Option          "MinSpeed"      "0.79"
#Option          "MaxSpeed"      "0.88"
#Option          "AccelFactor"   "0.0015"

Option          "SHMConfig"     "on"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option 		"XvHsync"	"-3"
	Option		"VBERestore"	"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by encompass on 2007-01-08
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)
Follow these instructions.
It looks like you ried to install the ati instructions.

---

### Post by encompass on 2007-01-08
And just to tell you... I just did the instructions over again and it seems to work fine.
You may have really screwed things up with the ATI stuff...
Not sure howt o get things back cause I don't know what you did...
You could try reinstalling... shouldn't hurt much to do it.

---

### Post by apakun on 2007-01-08
I tried but nothing is improved. The display is still hung when running beryl-manager, and "direct rendering: No"

---

### Post by encompass on 2007-01-08
I would just reinstall... if you want my help further.  I just have no idea.
It seems you did the install for the wrong card.  For some reason the ATI drivers.. if I am not mistaken, where installed.
I am not good enough to fix that problem.

---

### Post by encompass on 2007-01-08
Got a better idea... check first if you have 3d support on your live cd... can you put that glxinfo output from there?
Thanks...
if you get a yes on the Direct render then I would do a re install.

---

### Post by apakun on 2007-01-09
> **encompass said:**
>  check first if you have 3d support on your live cd... can you put that glxinfo output from there?

Sorry that I don't understand your suggestion. How can I check for 3D support?
Here is my computer's specification: [https://usm.channelonline.com/maglobal/storesite/Products/Overview/?id=M003410111](https://usm.channelonline.com/maglobal/storesite/Products/Overview/?id=M003410111)

---

### Post by Interestedinthepenguin on 2007-01-09
I believe encompass means run ```
glxinfo | grep render
``` while you are running the LiveCD.

---

### Post by encompass on 2007-01-09
Boot the live CD
When you are started... from the terminal run...
```
glxinfo | grep render
```
and post the output here on this form.
That will tell me if you have out of the box 3d support.
Don't worry about installing the cd again.  I just want to confirm that 3d is not working on your computer.

---

### Post by apakun on 2007-01-10
Here you are:

```

ubuntu@ubuntu:~$ glxinfo | grep render
libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20050225
```

---

### Post by encompass on 2007-01-10
OK looks like we have support from the live cd.... this can mean only one thing to me... somehow the accel was lost from something that was done.
To my knowledge it looks like you tried to install the ati drviers.

You have two solutions...

Fast and Quick sometimes painful... kinda like pulling hair
Reinstall your base system.  Simple as that.  Be sure to back things up as usual.
Slow and Painful always painful... kinda like pulling teeth
Try to figure out what you did and undo it.  I am willing to try to help but I don't we will get far.

---

### Post by apakun on 2007-01-10
I have chosen the first solution and... do you know how happy I am now? 
I have spent almost a month for that.

Many thanks to you.

---

### Post by encompass on 2007-01-10
Congrats, I am glad it is working for you.

---

### Post by erv2 on 2007-01-10
i m quite interested in the performance of GMA 950, is it good enough to coupe with XGL?

as i want to buy a new laptop and install ubuntu with Beryl on it.

thanks.

---

### Post by encompass on 2007-01-10
The performance is fantastic... I can even run tremulous at the same time at about 30 or 40 frams a second.  so it works great.
I lie it alot, most of all, because they are supported unlike ati and nvidea.
950 is the chipset... 945 is the graphics.

---

### Post by mortoss on 2007-01-12
Hi!

I've intel GMA running under Kubuntu EE, and 

```
glxinfo | grep render
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

:(

Could You post here working xorg.conf file?  Thx

---

### Post by encompass on 2007-01-12
It should be there... above.  Both work.
I don't know what people are doing but it seems that if you don't know what you did to break it.  Reinstall... sounds bad.  But true.

---

### Post by mortoss on 2007-01-13
```
I don't know what people are doing but it seems that if you don't know what you did to break it. Reinstall... sounds bad. But true.
```

What I did is that I use Adept to make my Kubuntu up to date. Perhaps I have bad repos... It's really weird...

/edit

I added 'load "dri"' to xorg.conf. Now:
```
glxinfo | grep render
libGL warning: 3D driver claims to not support visual 0x5b
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20050225
```

3D apps run faster ;) But I think it should be better - I suppose not enough of RAM is being shared with GPU (always 7MB ? )

glxgears - only 650fps in window mode ;/

---

### Post by mortoss on 2007-01-13
Now things got even more strange. Some 3d apps like Google Earth still jam, hang for few seconds and work again... But if i ran glxgears in backround - not only I don't get less performance - but then 3d apps work perfectly fluid? Why? Any ideas??

---

### Post by encompass on 2007-01-13
Not a clue dude.  I wish I knew this stuff better.

---

### Post by SyberKowboy on 2007-07-12
You know this stuff way better then some of us. Thanks for the the xorg.conf file. it work to clear up my poor acceleration issues with beryl, Works beatiful now even with AWN. On anther not do you have any issues with video in full screen? For some reason I get a really bad lag? Any ideas. I don't think it's the acceleration or xorg.conf but what could it be? Thanks again!

---

### Post by ii bk ll on 2008-04-30
I am having the same issues but when I run

glxinfo | grep render

I get this

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

---

