---
title: "Beryl - Radeon X1100 Specific Thread"
date: 2007-02-15
forum: Desktop Environments
---

### Post by staeryatz on 2007-02-15
**Introduction**
First off, I know there's tons of Beryl threads but none of them have much useful info on users with the Radeon X1100. I have reason to believe my problem may have to do with the hardware, so I created this new thread. I've closely followed some very great guides for XGl+beryl+edgy+radeon, but no luck.

**X1100 Background**
You may skip reading this part if you are already familliar with the X1100. The [[COLOR="Red"]Radeon X1100[/COLOR]]("http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_14603_14624%5E14627,00.html") is common on newer low-end notebooks (eg. < $1000), typically AMD Turion 64. It is detected by Linux as an X200M, but I've read it's actually an X300 chip downclocked, and added support for new power management features. The ATi drivers page doesn't list any drivers for the specific model X1100, but does list the X200 (not X200M) and the Mobility X300 which are the two closest models to my knowledge. I just used the fglrx drivers from synaptic because I was unsure, but the version is outdated (8.28.x vs 8.33.x).

**Experience**
Although I am fairly new to Ubuntu, I have been using and developing software for GNU/Linux since 1999, using various distro's. I'm not a newbie, I'm not a guru, I am somewhere in between.

**Problem (XGl)**
I can start the XGl server, and therefore the gnome desktop in XGl, but it is guaranteed to hardlock my system within a few minutes of use. Trying to start beryl doesn't work at all and I get hardlocks so I can't get a backtrace from the command line. I have tried options in the xorg.conf file which others that claimed to have fixed hardlocks on some Radeon cards, but it made no difference at all. I've given up on XGl completely because of its instability.

**Problem (AIGLX)**
I can start X with AIGLX by enabling composite (beryl will fail if composite is not enabled), which in turn disables DRI unfortunately. When I start beryl, it runs its checks and it fails at checking for non-power of two texture support.[COLOR="Red"] *Correct me if I'm wrong, but isn't non-power of two texture support a **hardware** feature?*[/COLOR] Which would mean there's no possible way to meet this beryl requirement with an X1100?

**My Setup**
Ubuntu 6.10 (Edgy) AMD64 Desktop
Linux 2.6.17.11
fglrx driver 8.28.08
x.org 7.1.1
Acer Aspire 5050-5554 notebook featuring:
AMD Turion 64-X2 TL50 (1.6GHz)
ATi Radeon Xpress 1100 (128MB shared memory)
1GB DDR2 533MHz

[COLOR="Red"]**Update**
Looks like it works, problem solved, thanks to hizaguchi. Here are the links to some of the guides I was using:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)[/COLOR]

---

### Post by patrickfromspain on 2007-02-15
I'd try to install the latest drivers from the ati site.. maybe those fix your issues.

---

### Post by staeryatz on 2007-02-15
Yeah I'll try that but my card isn't listed among the supported cards for linux drivers on the ATi site. What I want to know is what kind of driver setups do the *other X1100 users* have, and if it works for them.

---

### Post by staeryatz on 2007-02-15
Well, I gave it a shot and installed the latest 8.33.(6?) drivers Mobility X300 drivers from the website. BAD IDEA.

Beryl+AIGLX still has the same issue with the non-power of two texture support. Forget Beryl+XGl, the XGl session won't even load now. Completely aside from Beryl or XGl, just simply logging ouf of a regular gnome session will not return me back to gdm, but hardlock on a blank command line screeen.

At this point, I figured that I'm better off with the 8.28.08 drivers. I reverted back to them, and the corresponding kernel modules, however now my DRI didn't work at all anymore.

---

### Post by hizaguchi on 2007-02-20
You need to use the proprietary fglrx driver, which does not yet support AIGLX, so you're stuck with XGL.

First thing you need to do is install the driver
```
sudo apt-get install xorg-driver-fglrx
```

Then you need to tell X to use it by editing /etc/X11/xorg.conf or with
```
sudo aticonfig --initial
```

While you're at it, since AIGLX isn't supported by fglrx, you need to edit your xorg.conf to disable the composite manager and AIGLX.  You can do that by adding this to the end:
```
Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection
```
Also make sure that the DRI mode is set to 0666.

Finally, you need to make a symlink so that (I think) X can find your dri module
```
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```

It's probably a good idea to reboot, or at least restart X with CTRL-ALT-BACKSPACE now.

Then you can use commands like glxgears (should now run smoothly), glxinfo, and fglrxinfo to verify that everything is working and that you have 3D acceleration.  If that's all good, you just need to follow the guide on the Beryl wiki and everything should work.

---

### Post by staeryatz on 2007-02-20
Dude, TYVM!!

I've tried everything about a dozen times, except the command:

sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri

to make the symlink. Looks like that made it work. :D

It looks like my XGl wil not start when I have dual monitors enabled though.

---

### Post by tuque on 2007-02-25
Ah now this is a tease!. I have the very same make and model laptop. I am still struggling to get Beryl working properly on a new install of Edgy 64bit. 
If I try to log into an XGL session the Desktop is frozen. Trying to select the Beryl Window Manager from a regular Gnome session also fails and reverts back to Gnome.
 I have followed the instructions on the links you mention. I'm obviously doing something wrong or missing something. 
Would you mind detailing exactly what steps you took to get Beryl running please?

Many thanks

---

### Post by staeryatz on 2007-02-27
It's hard to give the exact steps on what I did or in which order, becuase I've tried getting it to work dozens of times, switching up little things in steps here and there.

1) The last (and thus working) thing I did to config my video drivers was method 2 from:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

1.5) Make sure to disable dual monitor setup. Beryl doesn't seem to work with "Big Desktop". It may or may not work with other dual monitor methods like FBMerged or Xinerama, but for simplicity sake, let's try to get Beryl working with one monitor for now.

2) Then the last thing I did for xgl was verify that everything in *this* guide matched my configuartion (except regarding ati driver installation). I double checked all files to make sure their content matched the guide, correct permissions, and correct filenames:
[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

Tip: I actually did correct a filename, becuase at one point I used two different Beryl guides. I had the xgl session file point to /usr/bin/startxgl.sh, while the filename was /usr/bin/startxgl. That really messed me up until I caught the mistake.


3) And finally, hizaguchi's suggestion:

sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri

And in the xorg.conf file:

```

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection

```


After restarting X, I was able to run XGl + Beryl. But it won't work with Dual monitors setup so I haven't really been using Beryl, because I'd rather have my 14" laptop output to a 19" widescreen LCD.

So all I can say is double check your system for everything mentioned in those two guides that it all matches. That's the last thing I did before it started working. Good luck.

My xorg.conf file:
```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "ServerLayout"

	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "dbe"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"

	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Driver      "fglrx"
	Option	    "DesktopSetup" "single"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS482)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x800"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x800"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection


```

---

### Post by tuque on 2007-02-27
Thank you staeryatz,

I got it working,  thanks to your kind assistance.
I appreciate the time and trouble you went to in your reply.
In my case I was simply using the old video drivers. I installed drivers 8.34.8, following method 2 as detailed in ; 

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

And it worked!.

Oh boy is this Beryl desktop addictive or what! It's incredible.

Many thanks to all working on this Beryl project.

---

### Post by staeryatz on 2007-02-27
Aweome! Ooooh i didn't know they got newer drivers (8.34.8).

/me installs them now

---

### Post by smgk on 2007-03-05
Staeryatz,
	Thank you very much for posting your experience. I got beryl running with the help of the steps you have out lined above.

   I have an almost identical laptop as you do.
(details below so google can find your post for this laptop)
Acer Aspire 5100 laptop
AMD Turion 64-X2 (1.6GHz)
ATi Radeon Xpress 1100 (detected as 200M, but I am told its a 300M chip)
1GB DDR2 533MHz

I had to make 2 minor changes to actually get Xgl to load on my laptop.

I) symptom:   "Xgl" was not listed in the list of sessions by gdm. instead a new entry "foo" appeared in the list.
This is a cosmetic thing not functional problem
The cure:
  This is relevant to step 2 on [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")
  Notice that xgl.desktop is only few lines and gnome.deskop has all locales defined.
  (a tip from [http://wiki.archlinux.org/index.php/Xgl]("http://wiki.archlinux.org/index.php/Xgl") )
  I made a copy of gnome.desktop and changed only the relevant lines from lhansen's guide. saved this file as xgl.desktop.
  donot worry about other languages (other than the one you use. they can be any string)

II) symptom:  when I selected Xgl session and logged in, gdm complained that it cannot "Exec" something and pushed me to a failsafe gnome session.
The cure: LD_PRELOAD=/usr/lib/fglrx/libGL.so
	I added the above line to my startxgl script.
my startxgl script looks like this

```
#!/bin/sh
LD_PRELOAD=/usr/lib/fglrx/libGL.so
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

```
thanks,
-GK

---

### Post by dogmir on 2007-04-05
whenever i get to the 

sudo module-assistant build fglrx

step it will die at stage four and will not continue to build it does anyone have anythoughts?

edit: i got it to work now nevermind...

---

### Post by Jilbert on 2007-05-27
im still not able to run desktop effects could not be enabled error.
I have ATI Radeon Express 1100 and beryl version is beryl-core 0.2.1

---

### Post by alevensalor on 2008-02-26
I just wanted to thank the people who had the headache long before I did, the tips here worked for me as well. 

Thanks!
~Anthony

---

