---
title: "Google earth messed the X settings (have to login twice)"
date: 2007-08-01
forum: Desktop Environments
---

### Post by rafalr on 2007-08-01
After a fresh install of 32 bit Ubuntu 7.04 (on AMD 64, nvidia card) I started to install another non-repo 
software, including GoogleEarth. Before installing this everything went smooth and fine, but right after GE was on the machine, during the next reboot (and each following boot, till today) I observe the following:
- the Ubuntu login screen appears normally, but with cursor invisible
- after entering login/pass the background colour remains (while the rest of the screen disappears) for another 2 minutes, following that the screen briefly blinks black and returns to another login screed
- this time the cursor is visible, and after entering login/pass the X session starts.

I have removed Google earth completely, as well as any config/settings files it might have left that I found with "locate" command. This did not help at all.

I was then experimenting a lot with various nvidia drivers (nv, nvidia-glx, nvidia-glx-new) and various 
xorg.conf settings. This apart from having major problems with nvidia-glx and nvidia-glx-new (system complained it could not find the nvidia kernel modules) - but I sorted this out by installing nvidia-glx-new by Automatix2.

Anyway, regardles the diver installed and set in xorg.conf I still need to login twice. My gut feeling is that GE left some settings in one of the system files that forces system to look for some option that is not available so the system fails to launch x session, and only after the second login the system adjusts the option to the optimum value and starts successfully. GE is said to be not working with nvidia-glx well. I know this is only a guess and a very vague one, but it is as far as I could go. I am appending my curent xorg.conf as well as some system logs.

Any advice is precious as I have no other ideas to explore.

rafal

---

### Post by perspectoff on 2007-08-03
Google Earth kept crashing/logging me out until i discovered the problem wasn't with Google Earth but with my graphics card driver settings.

I found out that the Ubuntu installer had denoted "VESA" as my standard graphic card in /etc/X11/xorg.conf:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

However, my system has an Intel 865G chipset with Extreme Graphics 2.

The appropriate graphics driver is i810, not VESA.

I therefore substituted the section:

Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

and changed the section:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
...

to
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics
...

Now both Stellarium and Google Earth work fast and without problems.

The problem seems to be that the auto-detection of my graphics card by the Ubuntu Feisty installation did not accurately identify the graphics card driver needed. This was not a problem in Dapper; I don't know what changed.

---

### Post by rafalr on 2007-08-03
Hi, 

I thought so to, so I played a lot with various driver versions and settings, but my settings seem to be OK for nvidia card:

```

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5500]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5500]"
    Monitor        "Generic Monitor"
    DefaultDepth    24

```

any other ideas ?
kuna

---

### Post by gurth4ng on 2008-05-02
I am having the same problem after upgrading from 7.10 to 8.04.

every time i boot up my computer i have to login twice.

I've read about this problem being reported on the net for diferent versions of Ubuntu, so my guess something is messing up the login proccess during the upgrade?

which file is responsible for what happens during (after) the user login? maybe the answer is there..

---

### Post by rafalr on 2008-05-02
Hi,

I managed to solve this (or it solved itself - I am still not 100% positive about that).

What was most possibly the issue is that:
- only after login the X server / Gnome fully loads all config settings but before that some default settings are being "guessed" by system
- in my case most possibly the screen/monitor resolution was "guessed" not properly and needed another "guess" (= X server re-start)
- you can change the screen resolution used for login purposes manually in /boot/grub/menu.lst (I am quoting this from memory, could be slightly different) where in the end of the line describing your kernel you need to add parameter describing the resolution your screen likes best (it is just a 3-digit number, in my case it was 792 ? - again from memory)
- or you can change this using GUI called Startup Manager (can be installed from repos)
- of course before changing the settings you should check which resolution is recommended (there is a command for that I forgot, but you can also simply experiment with various resolutions to see which is best/safe)

edit: actually this is what you are most probably looking for:
[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

hope this helps
Rafal/kuna

---

