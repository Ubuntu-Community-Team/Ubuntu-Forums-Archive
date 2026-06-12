---
title: "How to change screen resolution on Ubuntu 8.10 genome"
date: 2008-11-27
forum: Desktop Environments
---

### Post by threshold on 2008-11-27
Hello everybody!

I'm new in this thread and had just successfully installed Ubuntu 8.10 on my 8 year old Hp532n desktop.

My problem is I cannot change the resolution on my screen from its default 800x600 setting. My screen can support up to 1280x1024.

Please..I am asking anybody who happens to know any solution for this problem, I appreciate your help.

Thanks you in advance

my set-up:

Processor : amd athlon 1800
Graphics  : Integrated nvidia geforce2
dual boot xp/ubuntu

thanks..treshold

---

### Post by Swagman on 2008-11-27
Well.. Apparently Xorg.conf is no longer used in 8:10 but mine still has it..

Here is a message from within it. I haven't run it myself but It only looks like a dpkg reconfigure.

> 
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg


So I guess you open a terminal and type
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Your Xorg.conf file can be found & edited (**if you want a butchers at it before fiddling**) by opening a terminal and typing

```
sudo gedit /etc/X11/xorg.conf
```

xorg makes an auto backup so your original would be called xorg.conf.1

Mine looks like this....



> 
#   sudo dpkg-reconfigure -phigh xserver-xorg

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"gb"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection


I noticed in Failsafe it has this entry towards the bottom

> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection



Maybe yours is running in failsafe ?

You could probably add a resolution yourself where it says "800x600"

---

### Post by m_l17 on 2008-11-27
Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=975058]("http://ubuntuforums.org/showthread.php?t=975058")

You will have to use the Terminal for this to work. Take a look at this if you don't know:

[https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal")

---

