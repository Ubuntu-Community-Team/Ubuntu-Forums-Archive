---
title: "Old NVidia driver problems, brand new to Ubuntu"
date: 2007-01-14
forum: Gaming &amp; Leisure
---

### Post by EvilMarshmallow on 2007-01-14
Hello all,

I started making my switch to Ubuntu (Edgy) about 3 weeks ago.  So far I've found everything I need to know compliments of our friends at Google :) 

I've got an older card... a GeForce 3 Ti 200 in this box.  Ubuntu automatically configured something for me upon install but it was a basic VGA driver, didn't use the video card at all.  So I set about finding out how to install drivers from NVidia.  

I found the proper release number 1.0-96xx on their site, downloaded the file, and got it to run.  It said that it would need to compile a kernel for this driver, so I clicked ok.  It said that a kernel couldn't be found on their site but then it built one itself.  It then installed the driver without any problems.  However, when I rebooted, I get a message that says my kernel is incorrect for this driver and won't start GDM.  The number on the current kernel is 1.0-76[something, i think 18?].   I can't find whatever it is I'm supposed to download.  I tried to use my old x11 config (the installer backed it up for me) but it won't let me start GDM at all...  Can you help?

---

### Post by PisstMSTRCHIEF on 2007-01-14
Whenever I was messing with drivers and i broke something i usually ended up reinstalled ubuntu, lol. The only thing I can suggest is just keep trying something different until something works. 

I don't know if this applies but while installing video drivers i had to hit ctrl+alt+F1 then install.

Sorry, I can't be more helpful. :???:

---

### Post by Count on 2007-01-14
Look for the envy script in the multimedia section, it's how I got my card to run, a NVIDIA RIVA TNT2. I don't have the link on-hand right now, but it should be easy enough to find.

Edit: here is the link to the thread, [http://www.ubuntuforums.org/showthread.php?t=301499](http://www.ubuntuforums.org/showthread.php?t=301499)

---

### Post by Fitzy_oz on 2007-01-14
> **EvilMarshmallow said:**
> Hello all,

I started making my switch to Ubuntu (Edgy) about 3 weeks ago.  So far I've found everything I need to know compliments of our friends at Google :) 

I've got an older card... a GeForce 3 Ti 200 in this box.  Ubuntu automatically configured something for me upon install but it was a basic VGA driver, didn't use the video card at all.  So I set about finding out how to install drivers from NVidia.  

I found the proper release number 1.0-96xx on their site, downloaded the file, and got it to run.  It said that it would need to compile a kernel for this driver, so I clicked ok.  It said that a kernel couldn't be found on their site but then it built one itself.  It then installed the driver without any problems.  However, when I rebooted, I get a message that says my kernel is incorrect for this driver and won't start GDM.  The number on the current kernel is 1.0-76[something, i think 18?].   I can't find whatever it is I'm supposed to download.  I tried to use my old x11 config (the installer backed it up for me) but it won't let me start GDM at all...  Can you help?

at the command prompt type the following

sudo dpkg-reconfigure -phigh xserver-xorg
This will allow you to reconfigure your x windows settings.  Look for the video driver nv and you should be right after that.  reboot the system and it should be ok.

After you get back in - goto synaptic package manager and enable the restricted repos (if you haven't already" and install the nvidia-glx legacy drivers - these support the the older GeForce ti cards (I have a geforce ti4200 in my other computer).  after it's isntalled.  At the command line type sudo nvidia-glx enable or something similar to that.  Should be right to go after that....

If not, we'll tryn something else :)

---

### Post by EvilMarshmallow on 2007-01-15
I ended up going the reinstall route.  I'm only out a few weeks' worth of work because I'm brand new to Linux.

However, this brings me back to the point where I was earlier... basic Ubuntu-setup VGA drivers running (I can tell because 3D stuff chokes and Call of Duty via WINE complains about OpenGL not being enabled).

I contacted tseliot and he pointed me to the envy script he wrote... Fitzy, you think it should be as simple as installing the nvidia-glx legacy?  Can you expand a little on what you mean by "restricted repos"?

My device manager shows the proper card with NV20 in front of it.  I assume that means it's using the NV driver instead of the nvidia.  Is this the case?

---

### Post by Fitzy_oz on 2007-01-15
> **EvilMarshmallow said:**
> I ended up going the reinstall route.  I'm only out a few weeks' worth of work because I'm brand new to Linux.

However, this brings me back to the point where I was earlier... basic Ubuntu-setup VGA drivers running (I can tell because 3D stuff chokes and Call of Duty via WINE complains about OpenGL not being enabled).

I contacted tseliot and he pointed me to the envy script he wrote... Fitzy, you think it should be as simple as installing the nvidia-glx legacy?  Can you expand a little on what you mean by "restricted repos"?

My device manager shows the proper card with NV20 in front of it.  I assume that means it's using the NV driver instead of the nvidia.  Is this the case?

You'll have to forgive the fact that the screenshot looks like im' using windows as I'm dumping the data remotely from work as I can't remember the exact pkg names or locations.  (It's been a long day at work)
Open Synaptic Package manager ------> Settings Menu  -------> Repositories.

Make sure they are all enabled, then click reload to refresh the repos.

Do a search for Nvidia - It should yield quite a few results for you.

Select the following packages for installation:

nvidia-glx-legacy
nvidia-Settings
nvidia-xconfig

In a terminal type sudo cp /etc/X11/xorg.conf /etc/X11/xorg.nvidia.back then type
 sudo nvidia-glx-config enable after it's all installed.  this should enable the driver.  After the reboot you should see the nvidia splash screen just before X starts up.  If the server fails.  type sudo cp /etc/X11/xorg.nvidia.back /etc/X11/xorg.conf to get your old config back.

Let me know if you have any more trouble.

---

### Post by EvilMarshmallow on 2007-01-18
Sorry for the delay, finally had some free time to work on this!

I only see a "nvidia-glx"... no "legacy" in my Synaptic window.

I pulled up a terminal and did

**sudo apt-get install nvidia-glx-legacy**

but I got an error:

[INDENT]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/INDENT]

I did see -settings and -xconfig in Synaptic and I already installed them.  No problems there.

---

### Post by EvilMarshmallow on 2007-01-18
Never mind that, n00b mistake of leaving synaptic open while trying to apt. :rolleyes: 

I get a different error message now:

[INDENT]Package nvidia-glx-legacy is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-legacy has no installation candidate
[/INDENT]

I assume this means I have to find it elsewhere.  Where can I look?

---

### Post by Fitzy_oz on 2007-01-18
jump to at terminal and type sudo apt-get update and the sudo apt-get refresh.  THen try synaptic again and search for nvidia

---

### Post by EvilMarshmallow on 2007-01-19
Ok, found it!

I installed it through synaptic... I've now got
[INDENT]nvidia-glx-legacy
nvidia-Settings
nvidia-xconfig[/INDENT]
all installed.

I went back to the console and typed in **sudo nvidia-glx-config enable **as you said to do, but I get the following:

[INDENT]Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.[/INDENT]

How can I find out what version of the kernel I have running?  Do I just install the kernel source package from Synaptic, or is there something else I need to do to it?

---

### Post by Fitzy_oz on 2007-01-20
> **EvilMarshmallow said:**
> Ok, found it!

I installed it through synaptic... I've now got
[INDENT]nvidia-glx-legacy
nvidia-Settings
nvidia-xconfig[/INDENT]
all installed.

I went back to the console and typed in **sudo nvidia-glx-config enable **as you said to do, but I get the following:

[INDENT]Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.[/INDENT]

How can I find out what version of the kernel I have running?  Do I just install the kernel source package from Synaptic, or is there something else I need to do to it?

Ah yes, the kernel module - install the nvidia-kernel-2.6.17-generic and nvidia-kernel-common.  Reboot and try the command again...
:)

---

### Post by EvilMarshmallow on 2007-01-20
I'm so close, I can almost taste it...

[INDENT]Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.[/INDENT]

This is what I get when I run **sudo nvidia-glx-config-enable**.

I rebooted before I ran the command again and I DID see the nvidia splash screen.  So at least we're making progress!

By the way, fitzy, thanks so much for your help. :KS I owe you a pint!

---

### Post by EvilMarshmallow on 2007-01-21
A little more information:

I couldn't locate anything labeled exactly what you said

[INDENT]nvidia-kernel-2.6.17-generic[/INDENT]

in my Synaptic.  The nvidia-kernel-common I found with ease.

The closest to the above that I found was **nvidia-legacy-kernel-source**.

I installed that package but I don't know if it compiled the kernel for me, or what.

Should I run the command in the above error message and see if it just needs to be coaxed into finishing the process?  Or did I do something wrong?

---

### Post by EvilMarshmallow on 2007-01-21
I ran the command

[INDENT]md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum[/INDENT]

and restarted X... it crashed.  I was able to restore my X session from the backup config I made.  Upon rebooting X again, I got a little error message that said "Unable to initialize HAL" but everything seems to be working ok otherwise.

](*,) 

Please help if you can!  I don't know what to do next!

*********  UPDATE ***********
I had forgotten to replace the

xorg.conf.md5sum

file when I was restoring from backup, the HAL message was because the bad version of the file couldn't mount my cdrom drives properly.  Restoring the old version fixed that.

---

### Post by Fitzy_oz on 2007-01-21
> **EvilMarshmallow said:**
> I ran the command

[INDENT]md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum[/INDENT]

and restarted X... it crashed.  I was able to restore my X session from the backup config I made.  Upon rebooting X again, I got a little error message that said "Unable to initialize HAL" but everything seems to be working ok otherwise.

](*,) 

Please help if you can!  I don't know what to do next!

*********  UPDATE ***********
I had forgotten to replace the

xorg.conf.md5sum

file when I was restoring from backup, the HAL message was because the bad version of the file couldn't mount my cdrom drives properly.  Restoring the old version fixed that.

hmmm, run sudo module-assistant and see if you get a menu that allows you  to build or install modules in the kernel - Im not in front of my linux box at atm but when I get there i'll try and draft up the whole process for you and Post a Document from start to finish :)

---

### Post by EvilMarshmallow on 2007-01-21
I got to the menu but every option returned an error and failed out... "GET", "BUILD", and "INSTALL".

---

### Post by Fitzy_oz on 2007-01-22
> **EvilMarshmallow said:**
> I got to the menu but every option returned an error and failed out... "GET", "BUILD", and "INSTALL".

Bare with me mate, I'm doing it on m work computer right now which has an mx440 in it which needs the same driver.

---

### Post by Fitzy_oz on 2007-01-22
> **EvilMarshmallow said:**
> I ran the command

[INDENT]md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum[/INDENT]

and restarted X... it crashed.  I was able to restore my X session from the backup config I made.  Upon rebooting X again, I got a little error message that said "Unable to initialize HAL" but everything seems to be working ok otherwise.

](*,) 

Please help if you can!  I don't know what to do next!

*********  UPDATE ***********
I had forgotten to replace the

xorg.conf.md5sum

file when I was restoring from backup, the HAL message was because the bad version of the file couldn't mount my cdrom drives properly.  Restoring the old version fixed that.

Did you run sudo nvidia-gxl-config after running md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum.  I think it has to be done again after md5 sum is verified...

Update:
Also run this command at the command prompt to install the compilation tools for the kernel.

Nearly there ;)

---

### Post by kvonb on 2007-01-22
Unfortunately it seems that you have been lead the long way around the problem!

Your card (Geforce 3) is not that old really, I use a Geforce 2 and TNT2 in some of my systems which makes yours sound quite new :).

I would suggest that you go through what you just did in this entire thread backwards to get your system back to where you started from!

Go to [www.nvidia.com]("http://www.nvidia.com") and follow the links for Linux drivers, look in the "Archive" section for driver version: NVIDIA-Linux-x86-1.0-9629-pkg1.run (it HAS to be that one!), download it and make it executable (right click and select properties or from a terminal: chmod +x NVIDIA-Linux-x86-1.0-9629-pkg1.run).

Logout of X, (if X doesn't work anyway, just do the next bit) then press <CTRL><ALT><F1> to get to the virtual terminal.


Login as your normal account, then type this lot:

```
 sudo vi /etc/default/linux-restricted-modules-common
```At the end of the file (use arrow keys to move the cursor), find the line:

```
 DISABLED_MODULES=
```Press the INS key once (to insert the following text)

Add "nv" in between the quotes, and make it look like:

```
 DISABLED_MODULES="nv"
```Now press the ESC key, then type this exactly:

```
 :wq
```Press enter, that lot will save and exit vi.

Now type this lot:

```
 sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
```(doesn't matter if it says already latest version etc', as long as it is installed)
```
 sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
``````
 sudo rm /etc/init.d/nvidia-*
``````
 sudo /etc/init.d/gdm stop
``````
 cd (to wherever the driver is located on your disk)
``````
 sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
``````
 sudo nvidia-xconfig --add-argb-glx-visuals
```(you might have to reboot at this stage if the next step fails)
```
 sudo /etc/init.d/gdm start
```That should now be working.

You could try all that on the Edgy install CD without messing with your hd install just to make sure it does work first, just don't do the reboot :).

Regards, Kev :)

---

### Post by Fitzy_oz on 2007-01-22
> **kvonb said:**
> Unfortunately it seems that you have been lead the long way around the problem!

Your card (Geforce 3) is not that old really, I use a Geforce 2 and TNT2 in some of my systems which makes yours sound quite new :).

I would suggest that you go through what you just did in this entire thread backwards to get your system back to where you started from!

Go to [www.nvidia.com]("http://www.nvidia.com") and follow the links for Linux drivers, look in the "Archive" section for driver version: NVIDIA-Linux-x86-1.0-9629-pkg1.run (it HAS to be that one!), download it and make it executable (right click and select properties or from a terminal: chmod +x NVIDIA-Linux-x86-1.0-9629-pkg1.run).

Logout of X, (if X doesn't work anyway, just do the next bit) then press <CTRL><ALT><F1> to get to the virtual terminal.


Login as your normal account, then type this lot:

```
 sudo vi /etc/default/linux-restricted-modules-common
```At the end of the file (use arrow keys to move the cursor), find the line:

```
 DISABLED_MODULES=
```Press the INS key once (to insert the following text)

Add "nv" in between the quotes, and make it look like:

```
 DISABLED_MODULES="nv"
```Now press the ESC key, then type this exactly:

```
 :wq
```Press enter, that lot will save and exit vi.

Now type this lot:

```
 sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
```(doesn't matter if it says already latest version etc', as long as it is installed)
```
 sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
``````
 sudo rm /etc/init.d/nvidia-*
``````
 sudo /etc/init.d/gdm stop
``````
 cd (to wherever the driver is located on your disk)
``````
 sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
``````
 sudo nvidia-xconfig --add-argb-glx-visuals
```(you might have to reboot at this stage if the next step fails)
```
 sudo /etc/init.d/gdm start
```That should now be working.

You could try all that on the Edgy install CD without messing with your hd install just to make sure it does work first, just don't do the reboot :).

Regards, Kev :)


Interesting - I didn't think the nvidia propr. drivers supported the gef3 period...

Update - Awesome it worked.  Nice one mate  :)

---

### Post by kvonb on 2007-01-22
>  Interesting - I didn't think the nvidia propr. drivers supported the gef3 period...

Update - Awesome it worked.  Nice one mate  :smile:

Excellent, glad to hear it worked :).

You can now go on to install Beryl if you are feeling lucky!  I have it running on my Geforce2/mx400 with that exact driver!

It is actually surprisingly fast as well, better than my old ATI 9200!

---

### Post by EvilMarshmallow on 2007-01-22
Ok, I got a much prettier nvidia splash screen this time.  The driver package asked me if I wanted to run nvidia-xconfig in a menu, I chose "Yes", rather than following the instructions listed (it offered to do a config backup, wasn't sure if i'd get that doing it the way shown).  Do I need to go back and run the command with

--add-argb-glx-visuals

on it?  I tried to run Billiard-GL (found it in Synaptic) and when I run the program it says it "Closed Unexpectedly".  So I'm guessing I'm not completely out of the woods yet...

---

### Post by kvonb on 2007-01-23
You dont HAVE to run the  --add-argb-glx-visuals, but you can if you like.  That is just for running Beryl or Compiz (don't even worry about those yet, it will complicate things too much!).

Run the "Nvidia Xserver Settings" util from Menu->Applications->System tools, and click on "OpenGL/GLX Information" in the left window pane, on the right it should say "Direct Rendering YES", if it does then everything is working properly, if not, then all I can suggest is try one of the other drivers which support Geforce3s from the Nvidia website, there is a link that tells which cards are supported, read that first.

If you have direct rendering working, try another game like Tuxracer or Enemy Lines which are in the add/remove progs thing.

Regards, Kev :)

---

### Post by EvilMarshmallow on 2007-01-23
You Aussies are the best!

With 9629 installed, I tried to click on the OpenGL info and the xconfig window crashed.  So I tried a different driver:  the 9631.  This one installed flawlessly, using the directions above, and 3d programs are running beautifully.

Thanks to both of you for your help!

---

### Post by Luffield on 2007-02-10
Great guide, kvonb. I'm trying to get Beryl to work on my system, which has a Geforce 2 card, and the drivers you recommended work well with it. It was a bit scary at times (apt-get will uninstall WHAT!?) but your guide is very accurate.

One problem that I did have was that the command
```
sudo rm /etc/init.d/nvidia-*
```
didn't do anything -- it said something like "not found" -- but I think it didn't make any difference, the drivers were installed.
Thanks!

---

### Post by chiriac ionut on 2007-02-11
Hello!!  Old Nvidia drivers had "refresh rate overwrite". This is very important and useful for a lot of games. Since 66.93 version the Nvidia drivers have not this feature anymore. I have a question for you: Do you know a new one which have this features or another program to do it?:confused:

---

### Post by honeybear on 2007-02-11
An easy way I installed a similar nvidia than yours:
 :guitar: 
I did this:

apt-get install xserver-xorg-video-nvidia  xserver-xorg-video-vesa  xserver-xorg-input-synaptics
xserver-xorg-input-mouse xserver-xorg-input-kbd x-window-system-core xserver-xorg 

Mdoules are very needed: apt-get install nvidia-kernel-2.6-686
  
```
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
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
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
	Option		"XkbLayout"	"fr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


Section "Extensions"
       Option "Composite" "Enable"
EndSection



```
my working xorg.conf for my nvidia

---

