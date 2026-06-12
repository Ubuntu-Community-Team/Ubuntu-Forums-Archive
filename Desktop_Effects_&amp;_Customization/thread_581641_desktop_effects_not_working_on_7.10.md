---
title: "desktop effects not working on 7.10"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by yang2iu on 2007-10-19
Hi, I just upgrade my ubuntu to 7.10 and the desktop effects do not seem to work.

It says "desktop effects could not be enabled". I'm using Intel card and the restricted drivers manager says it's enabled and in use.

Could anyone please help me out? I have no idea how to get it to work...

---

### Post by shogun301 on 2007-10-19
Go to System > Preferences > GL Desktop

Check the "Enable GL Desktop" box

If your effects are not already working, Go back into the Appearance menu where you were before and attempt to click on one of the buttons.

---

### Post by yang2iu on 2007-10-19
the weird thing is... I don't have "GL desktop" under Preferences... but shouldn't I have everything that I need by default?

---

### Post by shogun301 on 2007-10-19
Well, this has been a sore spot for me as well as other so far.  Try:

sudo apt-get install xserver-xorg

then press Ctrl+Alt+Backspace to restart your X

---

### Post by timcredible on 2007-10-19
if you're trying to use the 3d stuff, i think you have to have nvidia or ati.

---

### Post by Apothysis on 2007-10-19
I have the same problem on my laptop. It has a ATi Mobility Radeon X1400.

---

### Post by jmanl2006 on 2007-10-19
I am also having trouble with the  extra setting for appearance. Yesterday, right after i upgraded to 7.10, that setting was working beautifully. Today, even having the appearance setting on extra, the function where you hover your mouse in the top right and left corner does nothing when it worked the other day. I still have wobbly windows and fading or whatever.

---

### Post by shogun301 on 2007-10-19
I am running the Intel 945 Integrated chipset on an i810 driver and the 3D effects work just fine as long as you are only trying to use one monitor.

---

### Post by jmanl2006 on 2007-10-19
I tried that command and this is what i got:


Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

and the function still doesn't work.

---

### Post by shogun301 on 2007-10-19
try:

apt-get remove xserver-xgl

then restart your X session.

---

### Post by jmanl2006 on 2007-10-19
this is what i got


jeff@jeff-desktop:~$ apt-get remove xserver-xgl
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jeff@jeff-desktop:~$ 


im a REAL noob to linux or commands so i have no idea what this means


thanks

---

### Post by jmanl2006 on 2007-10-19
X session??

---

### Post by yang2iu on 2007-10-19
I tried both with and without xserver-xgl, but nothing seems to work... =/

---

### Post by PaulFr on 2007-10-19
apt-get and similar commands require **sudo** prefix. So ```
sudo apt-get <action> <parameters>
``` rather than ```
apt-get <action> <parameters>
```.

Anyway, please keep us updated on how it goes.

---

### Post by kevmaster on 2007-10-19
> **jmanl2006 said:**
> this is what i got
jeff@jeff-desktop:~$ apt-get remove xserver-xgl
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jeff@jeff-desktop:~$ 
im a REAL noob to linux or commands so i have no idea what this means


I don't know if removing your xserver-xgl will be the solution to your problem but as far as the Permission denied error goes, try:

```
sudo aptitude remove xserver-xgl
```

---

### Post by jmanl2006 on 2007-10-19
trying to remove xserver-xgl... (by the way.. what is xserver-xgl?)

jeff@jeff-desktop:~$ sudo aptitude remove xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      

still no progress even after doin that (sudo apt-get install xserver-xorg) command to install it


thanks for your help

---

### Post by yang2iu on 2007-10-19
I don't want to sound rude or something and I'm new to ubuntu/linux myself, but I posted this thread in the hope that I could find a solution to my problem, which is not how to 'sudo'... if anyone needs help on that, could you please start a new thread of your own somewhere? and I'd be happy to help, too...

---

### Post by jmanl2006 on 2007-10-19
Sorry about that, but to fix problems you have to go over some of the basics. I'll try not to get side-tracked. Remember, I want to get the same problem fixed.

---

### Post by khristian on 2007-10-19
If you have an ATI graphic card:
```
sudo apt-get install xserver-xgl compiz compizconfig-settings-manager
```
Restart your X Server (CTRL+ALT+Backspace, or simply logout and log back in). XGL should start automatically. Click with the left mouse button on the desktop and, if the menu fades in, it worked.

If you have a Nvidia graphic card, you can try the above without the xserver-xgl:
```
sudo apt-get install compiz compizconfig-settings-manager
```

Then restart the X Server as described above.

In Gnome you can change the settings for Compiz in System-> Preferences-> Appearance-> Desktop Effects.
For KDE, I'm still looking for it :P (didn't want to install all the gnome config tools)
Good luck!

---

### Post by pacofvf on 2007-10-19
First 1.- Install restricted drivers
system>administration>restricted Drivers Manager
then check the ati on gutsy or nvidia posts:)
thank you all guys i love my ubuntu

---

### Post by jmanl2006 on 2007-10-19
My menus fade and the windows have that 'wobbly' effect, but I don't have that function where you hover your mouse over the top right or left of the screen and the screen is either supposed to show all of the workspaces or all of the windows.

---

### Post by pt123 on 2007-10-19
> **shogun301 said:**
> Go to System > Preferences > GL Desktop

Check the "Enable GL Desktop" box

If your effects are not already working, Go back into the Appearance menu where you were before and attempt to click on one of the buttons.

I too don't have this and I am using the restricted Nvidia  drivers on my 6600GT card.

But then I couldn't enable the Visual effects, it would always fallback to none.
What is the command to get the visual effects applet from a terminal so I can see the error message.

In the new xorg.conf file all it has is this for device, miodule & screen
```

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1680	1050
		Modes		"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection


```

When I was on Feisty running Compiz perfectly using the drivers from the nvidia site,  device, module  & screen looked like this:
```

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "1680x1050_60 +0+0; 1152x864 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    #Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    #Option         "DisableGLXRootClipping" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

Do we need to manually add Option         "AddARGBGLXVisuals" "True"

---

### Post by nerkman on 2007-10-19
```
E: Couldn't find package xserver-xgl
```

I've tried all the suggestions in this thread (I have an ati card as well) and it says it cannot find the xserver-xgl package.  Is there something wrong with my repositories or something?

Where can I find this?  I've got the CD in the drive, but it's not reading it.

---

### Post by searayman on 2007-10-19
after doing this:

sudo apt-get install compiz compizconfig-settings-manager

compiz now i guesse starts cause i dotn get the message saying it hasnt.... but i have no window boarders....

any ideas?

---

### Post by totalnub on 2007-10-19
sudo apt-get install emerald

then, alt-f2 and type: emerald --replace

the problem is that emerald themes don't exist as a package for gutsy yet.

go to gnome-look.org and click on beryl, find a theme you want and DL it.

then you will need to open emerald theme manager (under preferences)

click import and navigate to where you DL'd your .emerald file(s)

---

### Post by searayman on 2007-10-19
> **totalnub said:**
> sudo apt-get install emerald

then, alt-f2 and type: emerald --replace

the problem is that emerald themes don't exist as a package for gutsy yet.

go to gnome-look.org and click on beryl, find a theme you want and DL it.

then you will need to open emerald theme manager (under preferences)

click import and navigate to where you DL'd your .emerald file(s)

ok that doesnt work an no output in terminal.... ALso although it doesnt say compiz can't start, I dont relly see any ffects even without window boarders...

---

### Post by yang2iu on 2007-10-19
sudo apt-get install compiz compizconfig-settings-manager

does nothing for me. still says couldn't enable effects.

---

### Post by roofoo on 2007-10-19
I too am having problems enabling the desktop effects. I have an nvidia geforce 7600, and a 1680 x 1050 LCD. Every time I try to enable the advanced effects, the screen blinks, then drops me back at the login screen. When I login again, it still says I am using basic desktop effects, the advanced effects won't work. I've tried all the suggestions in this thread so far and still can't get it to work.

---

### Post by yang2iu on 2007-10-19
where can I check if my 3d acceleration is on or not?

---

### Post by pillar_zhang on 2007-10-20
> **khristian said:**
> If you have an ATI graphic card:
```
sudo apt-get install xserver-xgl compiz compizconfig-settings-manager
```
Restart your X Server (CTRL+ALT+Backspace, or simply logout and log back in). XGL should start automatically. Click with the left mouse button on the desktop and, if the menu fades in, it worked.

If you have a Nvidia graphic card, you can try the above without the xserver-xgl:
```
sudo apt-get install compiz compizconfig-settings-manager
```

Then restart the X Server as described above.

In Gnome you can change the settings for Compiz in System-> Preferences-> Appearance-> Desktop Effects.
For KDE, I'm still looking for it :P (didn't want to install all the gnome config tools)
Good luck!

&#35874;&#35874;----------thanks

---

### Post by pillar_zhang on 2007-10-20
> **yang2iu said:**
> sudo apt-get install compiz compizconfig-settings-manager

does nothing for me. still says couldn't enable effects.
ATI
sudo apt-get install xserver-xgl
ctrl-alt-backspace then login in...

---

### Post by yang2iu on 2007-10-20
I tried to run it in terminal it and got the following output:

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

I'm using intel, not ATI, by the way...

---

### Post by yang2iu on 2007-10-20
And if I remove xserver-xgl, it gives me:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

---

### Post by Ub1476 on 2007-10-20
You don't need to run in a XGL session with Intel cards, so if it's installed go to:

System>Administration>Synaptic Packagemanager>Click Search (top right) and write in XGL. Scroll down to xserver-xgl, click on it and remove, then Apply.

Note: The square is green if it's installed.

If I remember correctly you have some basic effects, right? To get advanced effects first make sure your driver is installed. Go to..

System>Administration>Restricted Driver Manager>Make sure the Intel driver is installed.

Next, open Synaptic again, search for "compiz settings", and install the compizconfig-settings-manager (should be on top).

When it's installed, go to..

System>Preferences>Appearance>Visual Effects>Custom
and..
System>Preferences>Advanced Desktop Effects Settings

For the scale plugin (shows all windows on desktop) go to "Window Management" and check scale. Click on it and go to Actions>General to choose they key for it. 

There are also some nice scale extras in "Utility".

In "Desktop" you find the Cube. Many people like to use this, just remember to check "Rotate Cube" as well, and change the number of Desktops in General>Desktop Size

Good Luck:)

---

### Post by yang2iu on 2007-10-20
I already removed xserver-sgl and I don't have any effect :confused:

---

### Post by Ub1476 on 2007-10-20
Alright, can you post your xorg.conf file?

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by yang2iu on 2007-10-20
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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"vbe"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
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

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	0
	Vendorname	"Intel"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modelname	"Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x960@60"	"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"Intel 945"
	Busid		"PCI:0:2:0"
	Driver		"i810"
	Screen	1
	Vendorname	"Intel"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by Ub1476 on 2007-10-20
Your xorg looks okay.. 

It might be that your card is blacklisted (doubt it though), so try to run this in the terminal:

```
SKIP_CHECKS=yes compiz
```

---

### Post by yang2iu on 2007-10-20
```
yang2liu@yang2liu-laptop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
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
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

---

### Post by searayman on 2007-10-20
anymore on why i dont get window boarders and it seems that the effects don't work once they are turned on?

---

### Post by pt123 on 2007-10-20
if you did an upgrade you need to do a complete fresh install of compiz and remove emerald

My problems have been resolved more info on this thread:

[http://ubuntuforums.org/showthread.php?t=581119](http://ubuntuforums.org/showthread.php?t=581119)

---

### Post by searayman on 2007-10-20
i did a fresh install of gutsy

---

### Post by Morton's Red Stapler on 2007-10-20
> **khristian said:**
> If you have an ATI graphic card:
```
sudo apt-get install xserver-xgl compiz compizconfig-settings-manager
```
Restart your X Server (CTRL+ALT+Backspace, or simply logout and log back in). XGL should start automatically. Click with the left mouse button on the desktop and, if the menu fades in, it worked.

If you have a Nvidia graphic card, you can try the above without the xserver-xgl:
```
sudo apt-get install compiz compizconfig-settings-manager
```

Then restart the X Server as described above.

In Gnome you can change the settings for Compiz in System-> Preferences-> Appearance-> Desktop Effects.
For KDE, I'm still looking for it :P (didn't want to install all the gnome config tools)
Good luck!

worked great for me, i use an ati mobility x700 on my acer LT, the only thing is that i now have a weird borded around all my windows, it looks kind of cool, but would like to know if can remove them, or if it is a glitch, ty for your help though

---

### Post by Weezer on 2007-10-20
This is what I get when I sudo gedit /etc/X11/xorg.conf. I have CCSM, but clicking it won't open it, and I've enabled custom settings. Curiously, I don't have the advanced window settings under System>Preferences. I was hoping someone could help me out. 

I have n nVidia card and am using restricted drivers. (Trying to get Compiz Fusion to work). 

```
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
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
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection


```

---

### Post by jmanl2006 on 2007-10-21
I FIXED MY PROBLEM!! Horray!

All I did was go to Add/Remove Applications.... other apps.....and downloaded the CompizConfig Settings Manager. This app has sooooo many settings for the Compiz plugin that comes with gutsy that I enabled that 3d feature that I wanted and about thousand other features!

Horray I'm happy!  

:-D:-D:-D:-D:-D:-D

---

### Post by Morton's Red Stapler on 2007-10-21
i figured out what was causing those wierd borders around my windows, all it was was the reflection effects, they weren't for the cube reflection or anyhting, it looked kinda cool, but slowed things up a bit, so it you have a weird border just disable reflection effect, and they will be gone.:popcorn:

---

### Post by XNYE on 2007-10-22
> **Ub1476 said:**
> You don't need to run in a XGL session with Intel cards, so if it's installed go to:

System>Administration>Synaptic Packagemanager>Click Search (top right) and write in XGL. Scroll down to xserver-xgl, click on it and remove, then Apply.

Note: The square is green if it's installed.

If I remember correctly you have some basic effects, right? To get advanced effects first make sure your driver is installed. Go to..

System>Administration>Restricted Driver Manager>Make sure the Intel driver is installed.

Next, open Synaptic again, search for "compiz settings", and install the compizconfig-settings-manager (should be on top).

When it's installed, go to..

System>Preferences>Appearance>Visual Effects>Custom
and..
System>Preferences>Advanced Desktop Effects Settings

For the scale plugin (shows all windows on desktop) go to "Window Management" and check scale. Click on it and go to Actions>General to choose they key for it. 

There are also some nice scale extras in "Utility".

In "Desktop" you find the Cube. Many people like to use this, just remember to check "Rotate Cube" as well, and change the number of Desktops in General>Desktop Size

Good Luck:)


I don't have the compizconfig-settings-manager when I type compiz settings in the synaptic package manager.  The two packages I do get are named: libcompizconfig0; Desc: Settings Library for plugins - openCompositing Project.  The other one is libcompizconfig-backend-gconf; the description is the same as the previous one.

 Any help would be great.. Thanks.

---

### Post by dalexis on 2007-10-22
I upgraded my Dell Inspiron 600m to 7.10 and could not get Desktop Effects working.  I kept getting that "Desktop effects could not be enabled" message.  

Then I found something interesting - running "compiz --replace" displayed, among other things, a message indicating that the maximum resolution at which 3D effects could be enabled was 1024!!!  So I bumped my screen resolution down to 1024x768 and tried to enable desktop enhancements again.  And IT WORKED!

Here's where it gets just plain dumb.  With the desktop effects still enabled, I bumped my resolution back up to 1440x1024 expecting Compiz to crap out and get disabled again.  But no!  All of the desktop bling still worked!  Of course, once X gets restarted (reboot, log off/log on, Ctrl-backspace) it goes back to that hokey 1024 resolution check and disables Compiz.

What gives?  Did someone forget to remove some test code in Compiz??

---

### Post by uber_nerd11 on 2007-10-22
I am running 7.10 on a Vostro 1400 with the intel video card.  The restricted drivers program states that there are no restricted drivers for this card. Glxgears works on this card.  I tried the resolution change as mentioned above to no avail.  I have downloaded the compiz manager program.  Any suggestions?

---

### Post by Morton's Red Stapler on 2007-10-22
> **XNYE said:**
> I don't have the compizconfig-settings-manager when I type compiz settings in the synaptic package manager.  The two packages I do get are named: libcompizconfig0; Desc: Settings Library for plugins - openCompositing Project.  The other one is libcompizconfig-backend-gconf; the description is the same as the previous one.

 Any help would be great.. Thanks.

```
sudo apt-get install compizconfig-settings-manager
```
that should get you the settings manager

---

### Post by roadkill_cr on 2007-10-22
I, too, am having problems starting desktop effects.  I think my card might be blacklisted, but I don't know what that means (or if I can work around it somehow).  Here's the results of compiz:

```
dlew@hopo:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2992' found 
aborting and using fallback: /usr/bin/metacity 
```

I'm running an Intel 965; there aren't any restricted drivers for it (at least, none that Ubuntu tells me about).

I understand an integrated graphics card won't ever do that well with effects, but I still want to see what they do in the first place.

---

### Post by XNYE on 2007-10-22
> **Morton's Red Stapler said:**
> ```
sudo apt-get install compizconfig-settings-manager
```
that should get you the settings manager

It worked today... I don't know why it didn't work the last time I tried it... maybe I rebooted in between trying.  Got it installed, somehow, and all the 3D effects are working.  Thanks for the help... on to other problems!

---

### Post by Morton's Red Stapler on 2007-10-23
> **roadkill_cr said:**
> I, too, am having problems starting desktop effects.  I think my card might be blacklisted, but I don't know what that means (or if I can work around it somehow).  Here's the results of compiz:

```
dlew@hopo:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2992' found 
aborting and using fallback: /usr/bin/metacity 
```

I'm running an Intel 965; there aren't any restricted drivers for it (at least, none that Ubuntu tells me about).

I understand an integrated graphics card won't ever do that well with effects, but I still want to see what they do in the first place.

check out this forum post, [http://ubuntuforums.org/showthread.php?t=582112](http://ubuntuforums.org/showthread.php?t=582112) the intel 965 IS blacklisted, that means that compiz will not work on it without a code workaround, but the code is risky

---

