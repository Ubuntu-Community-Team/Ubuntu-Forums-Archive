---
title: "Desktop Effects rip apart my screen."
date: 2007-07-18
forum: Desktop Effects &amp; Customization
---

### Post by Jaynix on 2007-07-18
First.. a picture of what is happening.
[[IMG]http://img509.imageshack.us/img509/7797/brokerz5.th.png[/IMG]](http://img509.imageshack.us/my.php?image=brokerz5.png)

My video card: nvidia 7900gtx

I enabled the restricted NVIDIA Accelerated Graphics driver that Ubuntu suggested. I've been looking through resources online, and have managed to get my resolution to 1280x1024 by editing xorg.conf, but I still have this problem of the screen messing up when I go to enable desktop effects. I haven't done anything manual with drivers other than enabling the restricted one. Here is some info, any ideas?

glxinfo | head
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
```

xorg.conf ```

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
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Identifier	"nVidia Corporation G71 [GeForce 7900 GTX]"
	Driver		"nvidia"
	Busid		"PCI:5:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"940B"
	VendorName	"Samsung"
	ModelName	"Samsung SyncMaster 940B"
	Option		"DPMS"
	Horizsync	30-81
	Vertrefresh	56-75
EndSection

Section "Screen"
	Identifier	"screenRight"
	Device		"nVidia Corporation G71 [GeForce 7900 GTX]"
	Monitor		"940B"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen		"screenRight"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by Raineer on 2007-07-18
Very strange, I have that exact card and no issues.

I ended up using the "Envy" script to install the latest drivers for me, have you tried that or just using the default "restricted-drvers" from Ubuntu?

For sure, those drivers usually work fine but they are not the latest level. You may have something unique that will require a later level driver.

---

### Post by Jaynix on 2007-07-18
I'm relatively new to linux, but over the last week i've tried something out, including Envy. If I remember correctly, Envy worked fine, but I just don't know what all it does to my system, and if what it does is reversible if I have issues. I ended up tryin to mess around with dual monitor stuff and beryl stuff and got frustrated and just reinstalled linux.  Maybe I didn't have to, but I'm new to the way it works.

So did you run the Envy script after enabling the restricted driver? or how did you go about doing it? I'm also curious, what resolution display(s) do you use? Maybe you could help me out with that as well.

---

### Post by Hobo Joe on 2007-07-18
```

sudo aptitude install envy

```
Uninstall current drivers.
Install nvidia driver.

Reboot.

---

### Post by Jaynix on 2007-07-18
> **Hobo Joe said:**
> ```

sudo aptitude install envy

```
Uninstall current drivers.
Install nvidia driver.

Reboot.
I haven't manually installed any drivers. The only one I am aware of is the restricted one that I enabled in the Restricted Drivers Manager. Do you mean I should disable that? What will disabling it do? I noticed when I enabled it, it made some changes to my xorg.conf file (the timestamp was updated)

And by "install nvidia driver," do you mean do it by means of envy?

and on a sidenote, rebooting vs CTRL+ALT+BACKSPACE vs logout login?

---

### Post by Hobo Joe on 2007-07-18
Envy does a better job with the installs and the configurations, that's why i suggested uninstalling and reinstalling, both with Envy. Don't worry about the restrictred driver manager, you can ignore that.

Ctrl+Alt+backspace will work fine.

---

### Post by Jaynix on 2007-07-18
aptitude doesn't find any packages when "aptitude search envy"

Here's my sources.list```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.) 
## Medibuntu - Ubuntu 7.04 "feisty fawn" 
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs 
deb http://packages.medibuntu.org/ feisty free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

deb http://archive.ubuntu.com/ubuntu/ feisty-backports restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb http://www.virtualbox.org/debian feisty non-free
```
:?

---

