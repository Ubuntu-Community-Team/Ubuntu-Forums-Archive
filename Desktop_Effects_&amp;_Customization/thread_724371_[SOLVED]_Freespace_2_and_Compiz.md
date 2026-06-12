---
title: "[SOLVED] Freespace 2 and Compiz"
date: 2008-03-14
forum: Desktop Effects &amp; Customization
---

### Post by grahambo2005 on 2008-03-14
Hey All

I installed freespace2 last week, worked fine.

then today I installed Xgl and created a few files to set up the built in compiz (when ya go to system>display>effects) and there are 3 options

none

normal

Extra

So i clicked Extra a compiz started working a treat. but now when I try to run freespace2 i get this error

"The required OpenGL extension 'GL_EXT_draw_range_elements' is not supported by your current driver version or graphics card."

is this because I logged into gnome using Xgl? or because I have desktop effects enabled?

Can you let me know?
Im gonna try to gnome without xgl enabled. illlet you know how i get on.

Cheers

---

### Post by grahambo2005 on 2008-03-14
tried starting a normal session and running freespace... no joy.

Can someone let me know whats happened?

heres my output

graham@graham-desktop:~$ cd /home/graham/Games/FreeSpace2graham@graham-desktop:~/Games/FreeSpace2$ ./fs2_open.bin -mod mediavps -tbp -spec -env -glow -mipmap -2d_poof -ship_choice_3d -3dwarp -warp_flash -alpha_env -decals -missile_lighting -cache_bitmaps -snd_preload -fov 1.05 -ambient_factor 8
ERROR: "The required OpenGL extension 'GL_EXT_draw_range_elements' is not supported by your current driver version or graphics card." at graphics/gropenglextension.cpp:394
graham@graham-desktop:~/Games/FreeSpace2$ 

I also created there 2 files after I installed XGL

/usr/local/bin/startxgl.sh

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session


and this 

/usr/share/xsessions/xgl.desktop

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application

---

### Post by IsawSp4rks on 2008-03-14
For starters...what's your graphics card?  If it's ATI x#### and your have fglrx successfully installed then xserver-xgl doesn't need to be in operation and will cause conflicts with apps such as glxgears (and probably Freespace 2).  In my case (being the noob I am) I used xserver-xgl to enable compiz-fusion on ATI x1600 equipped lappy before I learnt about editing compiz config files to enable proper fglrx support and none of my glx apps (or 3d games) would work at all.  Once I removed xserver-xgl glxgears would run (instead of segfaulting my xserver) and my games worked properly.

Hope that helps.

---

### Post by grahambo2005 on 2008-03-14
that certainly did help

removed Xgl and behold... Free Space 2 works...

Ok so now what should I do to get desktop effects working without using XGL?

and you guessed correct about my graphics card, its a HIS Radeon X1650PRO 512MB (ATI)

can you point me in the right direction?

---

### Post by IsawSp4rks on 2008-03-15
[http://ubuntero.org/cochise/weblog/718.html](http://ubuntero.org/cochise/weblog/718.html)

Do step 12.

ie :-

12. Add the driver to compiz whitelist.

sudo gedit /usr/bin/compiz

Change:

# Driver whitelist
WHITELIST="nvidia intel ati radeon i810"

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"

You should be able to safely ignore all the other preceding and following steps as you already have the fglrx driver installed and compiz starts automatically with ubuntu 7.10.

Oh and make sure to install compizconfig-settings-manager via Synaptic so you can play with and configure all of the compiz settings including the Desktop Cube.  (this isn't installed by default in Ubuntu 7.10)

:)

---

### Post by grahambo2005 on 2008-03-15
I have done as you suggested.

rebooted the machine once the option has been changed in the file. still no joy.

I get an error saying:

"The Composite extension is not available"

when i click on normal or extra desktop effects

Very annoying

---

### Post by IsawSp4rks on 2008-03-15
Open a terminal and type "fglrxinfo" (without the quotes), tell me what it says (ie copy and paste into a post here in the thread).

In the same terminal type "sudo gedit /etc/X11/xorg.conf" (again, without the quotes)

find the Extensions section, it may look like this

Section "Extensions"
        Option  "Composite" "0"
EndSection

and comment out the Option "Composite" "0"

so it looks so

Section "Extensions"
#        Option  "Composite" "0"
EndSection

save and exit gedit

restart your ubuntu (or you can just restart the X Server by CRTL+ALT+BACKSPACE which will take you back to the login screen)

see if compiz works now.

If not I'd urge you to follow this guide:-

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

Good Luck.

---

### Post by grahambo2005 on 2008-03-15
fglrxinfo output

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6473 (8.37.6)

going to restart now

---

### Post by grahambo2005 on 2008-03-15
Ok I restarted

now im getting this error

"Desktop effects could not be enabled"........... (Very Descriptive)

does the output of fglrxinfo look correct?

---

### Post by grahambo2005 on 2008-03-15
Followd that wiki as you suggested... still no luck!

I decieded to check the Xorg log and see if anything thing in there might show me where the problem is

this error is in there
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering

I know for a that in the ATI drivers __driCreateNewScreen_20050727 does not exist anymore, it nos called __driCreateScreen
this must mean AIGLX is fricken old.

any ideas?

---

### Post by IsawSp4rks on 2008-03-15
OK,

can you post your xorg.conf please

---

### Post by grahambo2005 on 2008-03-15
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
	Option		"XkbLayout"	"ie"
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
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"BEKO-VJAZ1"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"BEKO-VJAZ1"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1280x720"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
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
EndSection
Section "Module"
	Load		"glx"
EndSection
#Section "Extensions"
	#Option		"Composite"	"0"
#EndSection

```

Ive also tried

```
Section "Extensions"
	#Option		"Composite"	"0"
EndSection
```

Thanks a mil for your help btw

---

### Post by IsawSp4rks on 2008-03-15
Your xorg.conf looks OK but I wonder which ATI fglrx driver you're using as the latest 8.3 doesn't need the glx module to be loaded anymore.

Did you try "Method 2: Install the Catalyst 8.3 Driver Manually" from the wiki.  In practice I've found that to be most effective way of getting my x1600 Mobility working in Compiz and Games.  Also I've tended to go back to the vesa driver (which has no 3D acceleration) between driver installs via the "sudo dpkg-reconfigure xserver-org" which allows you to revert to defaults for the Xserver.

Oh and no problem.  Hope whatever I'm posting is pointing you towards a solution,

---

### Post by grahambo2005 on 2008-03-17
hey dude i finally got this working (compiz and freespace2) by installing the driver manually

my fglrxinfo now reads

```
graham@graham-desktop:~/Games/FreeSpace2$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6958 Release
```

however.

When i select use compiz effects the effects themselves seem a little patchy and don't seem to run as smoothly as they did when using xgl

any ideas on this?

---

### Post by IsawSp4rks on 2008-03-17
hmmm....which driver did you install?

My driver version is higher than yours..that would probably explain the poor/sketchy OpenGL and Compiz performance.  

my fgrlx output with the 8.3 driver installed (what I'm currently using)

[B]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.1.7412 Release[/B]

That complies with the .deb files that are created as part of the 

**sudo sh ati-driver-installer-8-3-x86.x86_64.run --buildpkg Ubuntu/gutsy**

command as part of the wiki I posted earlier

the .debs it creates as a result of running the command 
[B]
fglrx-amdcccle_8.471-0ubuntu1_i386.deb
fglrx-kernel-source_8.471-0ubuntu1_i386.deb
xorg-driver-fglrx_8.471-0ubuntu1_i386.deb
xorg-driver-fglrx-dev_8.471-0ubuntu1_i386.deb[/B]

- I just redownloaded the file:- 

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-3-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-3-x86.x86_64.run) 

and ran that command to check if something got screwed up elsewhere - it all seems to have worked well.

As you can see, the .deb files' version number relates to the fglrxinfo output (I suppose 2.1 == "8.4" in ATI's labs?)

Did you use this command
[B]
sudo dpkg -i xorg-driver-fglrx_8.471-0*.deb fglrx-kernel-source_8.471-0*.deb fglrx-amdcccle_8.471-0*.deb[/B]

when you installed the driver?

Hope this takes you another step closer.

---

### Post by grahambo2005 on 2008-03-17
I installed it today

I actually used a system tool to do it for me

I am using linux mint btw, its a distribution of ubuntu

the program is called envy and its sets up your graphics cards whether they are nvida or ati

the program ran ok. its installed the ati driver version 8.42.3

---

### Post by IsawSp4rks on 2008-03-17
Ahh that explains it.  I used Envy initially but find it buggy when removing/uninstalliing drivers and don't like that it restricts you to certain drivers.  I tried Envy recently, when the 8.3 was released and it didn't download the latest driver but feedback on Mint Planet site  says that this has recently been fixed.

[http://linuxmint.com/planet/2008/03/06/](http://linuxmint.com/planet/2008/03/06/) (the last link)

Make sure you grab the latest version if you're determined to use Envy:-

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) 

Also, some forum feedback that backs that up - [http://linuxmint.com/forum/viewtopic.php?f=49&t=10555](http://linuxmint.com/forum/viewtopic.php?f=49&t=10555)

I think if you follow the wiki guide I posted to the letter you shouldn't have issues (Mint is a derivative of Ubuntu and all the commands listed in the guide are supported by Mint) and you'll certainly be getting the latest driver installed.  

Good Luck.

---

### Post by grahambo2005 on 2008-03-21
I did as you suggested and downloaded the latest version of ENVY

installed driver 8-3

worked a treat

effects are working perfectly

one thing I will say though that when reading the documentaton its states that the driver and evy must be uninstalled before upgrading to OS version 8.X

you must then down laod EnvyNG

to anyone thats reading this ENVY has really worked for me. it was very painless. would 100% recomend it

Cheers
Graham

---

