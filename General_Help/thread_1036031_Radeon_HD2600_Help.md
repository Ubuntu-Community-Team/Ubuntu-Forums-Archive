---
title: "Radeon HD2600 Help"
date: 2009-01-10
forum: General Help
---

### Post by beattyml1 on 2009-01-10
I have been having the following problems with my graphics card (Radeon HD 2600) since I upgraded to 8.10:
1. video playback flickers when done while compiz is running
2. hangs when switching users (must kill power, and reboot)
3. my computer just doesn't feel right, feels slower and less stable(just a hunch on this one)

problems one and two were also cited by other users with the same video card

I was thinking about getting a new video card but was wondering if there are any workarounds etc before I go out and buy another video card 

I am currently using the proprietary drivers from ati 

any help would be appreciated

---

### Post by noob named chaz on 2009-01-12
hi I'm new to this hole Linux thing i got a bit board of vista and had herd of ubuntu from a friend. 
i have the same graphics card (but i have 2 in order to run three screens) and need HELP. i tried the suggested one in the hardware drivers thing(ATI/AMD proprietary FGLRX graphics driver) but it just crashed gnome and i had to do a full reinstall of ubuntu to get it up and running again. were can i find drivers and how do i get them to work.

---

### Post by beattyml1 on 2009-01-17
Anyone? If I don't get a reply soon I'll probably just go with a new graphics card, but please if anyone knows how to fix this I would really rather not have to shell out another $60-70

---

### Post by FIONEX on 2009-01-17
haha not necessary to buy a new card!

Run this in a terminal:
```
sudo gstreamer-properties
```
Enter your password and hit enter.

Then go to the video tab.  For the default output, select "X Window system (No xv)".  Then click close and your videos don't flicker.

In terms of the login screen hanging, you'll have to precisely describe when it hangs (what do you see last?).  Also, did you install ubuntu 64bit?  U'll have to diagnose the problem.  I'm running the 2600 XT with NOOO problems.  My system runs amazing!

---

### Post by FIONEX on 2009-01-17
> **noob named chaz said:**
> hi I'm new to this hole Linux thing i got a bit board of vista and had herd of ubuntu from a friend. 
i have the same graphics card (but i have 2 in order to run three screens) and need HELP. i tried the suggested one in the hardware drivers thing(ATI/AMD proprietary FGLRX graphics driver) but it just crashed gnome and i had to do a full reinstall of ubuntu to get it up and running again. were can i find drivers and how do i get them to work.

First of all, click on "System -> Administration -> Synaptic package manager".  It'll ask you for your password, so enter it and click ok.  Then the package manager will open. Click "reload" then when it's done, click on "Mark All upgrades".  Then click apply and let it do its thing.  Then restart to make sure your system is running the updated kernel.  Then install the graphics driver as you did earlier!

---

### Post by beattyml1 on 2009-01-17
I am running 64-bit
I'll post again when I get a chance to recreate the login problem

---

### Post by lavinog on 2009-01-17
what proprietary driver are you using?
the one installed with the restricted driver manager is 8-11 beta
8-11 and 8-12 works much better.
1-09 should be out any day now...most likely next week.

---

### Post by beattyml1 on 2009-01-20
The last thing I see is the normal gnome desktop, as soon as I click on a user name from the gnome panel user menu he screen goes black and then just stays there

I am using the driver that the proprietary driver manager uses (System->Administration->Hardware Drivers)

I also tried messing around with EnvyNG (qt graphical) but just ended up making things worse and went back to the proprietary driver manager manager

---

### Post by beattyml1 on 2009-01-20
Btw way how would I change the driver version

---

### Post by lavinog on 2009-01-20
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)
this has generally been a helpful site for installing the latest driver manually ( *Installing the restricted drivers manually *).
When installing the latest driver, just executing the install file usually works for me with no problems (*sudo bash ati-driver-installer-8-12-x86.x86_64.run*).
It used to be that you had to install it manually...and for some systems you still do.
Installing it the manual way can also give you a better understanding on how the driver gets installed and activated.
It is also a good site for troubleshooting/getting work arounds for the common issues.

---

### Post by honkatonk on 2009-01-23
i installed Ubuntu 8.10 a couple of days ago, and I'm pretty much a complete linux noob, but I'm picking up a few things.

anyway, I have the HIS Radeon HD 2600 XT 512MB card and I'm running a 64-bit system, and I installed proprietary linux drivers (first 32-bit then 64-bit), and I'm able to run most programs fine and my visual effects are on Extra without a problem. However I installed a couple of games like Nexuiz and Alien Arena and when I run them, my monitor displays the "Video Mode not supported" message, but background sound still works, and the only thing I can do restart through the ctrl-alt-F1 console. 

i tried downloading and installing drivers through EnvyNg after ATI drivers failed me, and it didn't work. I know that 3d graphics work, because i ran that 3d gears test thing (sorry, forgot what it was called, maybe glgears) and it didn't freeze or have any artifacts.  Can someone please help, because I have no idea what the problem is.

---

### Post by lavinog on 2009-01-24
The issue I think has more to do with the driver that came with intrepid.
Your card should be fine, and you should see many of these issues clear up with each driver update (there will be an update each month.) Many issues exist with ATI drivers because in the past ATI didn't really support the open source community...since AMD took over there have been great advances in linux support for ATI cards. Support is quickly catching up to other manufactures.

I don't know what driver envy installs...I don't think it is the latest driver either.
Have you tried the website that I posted.
I think many of the issues with the intrepid driver were solved by running the 3d software as root. (normally this is not recommended, but I would say try it out and see if it does work.) To run a program as root use sudo program name

---

### Post by honkatonk on 2009-01-25
> **lavinog said:**
> I don't know what driver envy installs...I don't think it is the latest driver either.
Have you tried the website that I posted.
I think many of the issues with the intrepid driver were solved by running the 3d software as root. (normally this is not recommended, but I would say try it out and see if it does work.) To run a program as root use sudo program name

Yeah, I'm currently trying to install an open source RadeonDriver, but I'm kind of failing at that. Running the software under root doesn't solve my problem, because Ubuntu installed games (like Nexuiz, for example) run under root, and I still get the "Video mode not supported".

At this point I'm pretty sure that it's just running under a wrong refresh rate that my monitor doesn't support, and hopefully the open source ati driver would fix that, but I'm having a lot of trouble installing it.

I'm using [_this guide for installing RadeonDriver_]("https://help.ubuntu.com/community/RadeonDriver") and I pretty much configured the driver, but I couldn't test it, because glxinfo doesn't work after I uninstall the fglrx driver....i have no idea what to do

---

### Post by lavinog on 2009-01-26
> **honkatonk said:**
> Yeah, I'm currently trying to install an open source RadeonDriver, but I'm kind of failing at that. Running the software under root doesn't solve my problem, because Ubuntu installed games (like Nexuiz, for example) run under root, and I still get the "Video mode not supported".

At this point I'm pretty sure that it's just running under a wrong refresh rate that my monitor doesn't support, and hopefully the open source ati driver would fix that, but I'm having a lot of trouble installing it.

I'm using [_this guide for installing RadeonDriver_]("https://help.ubuntu.com/community/RadeonDriver") and I pretty much configured the driver, but I couldn't test it, because glxinfo doesn't work after I uninstall the fglrx driver....i have no idea what to do

Is there a way to see what video mode it is trying to use? some monitors will tell you when you press the menu button.
I don't know if the opensource driver in the repos can handle 3d yet.

---

### Post by honkatonk on 2009-01-26
> **lavinog said:**
> Is there a way to see what video mode it is trying to use? some monitors will tell you when you press the menu button.
I don't know if the opensource driver in the repos can handle 3d yet.

No my monitor doesn't respond to any buttons on the screen besides the on/off when it displays "Video mode not supported". Under the open source  ATI driver, it doesn't even display the error, because it doesn't launch the program. I decided to run nexuiz in the ctrl-alt F1 console, just to see what it says and to see where the program occurs and it loads the game up to the point where it starts i guess opening or launching Direct Frame Buffer. The error goes something like this (might not be completely exact words, just some notes i jotted down on a piece of paper):

```
Direct/Util: opening /dev/fb0 and dev/fb/0 failed
   no such file or directory
DirectFB/FBDev error opening framebuffer device!
Use fbdev option or set FRAMEBUFFER environment var
DirectFB/Core: could not initialize 'system' core!
Quake error: Failed to init SDL video subsystem
DirectFBCreate: Initialization error!
```

I tried creating /dev/fb0 and dev/fb/0 didn't work. I tried installing anything with FB or framebuffer from the repository. Nothing. I added in the option to "useFBDev" in xorg.conf Device section, and nothing. tried fbdev command in the console and it doesn't exist.


Whatever, I chose to give up, because I have pretty much no knowledge or understanding when it comes to Linux, and it took way too much time to not get anywhere pretty much for nothing. I have XP dual booted for games, and the video playback problem isn't that bad...I guess sometimes you can't have a cake and eat it too, so I decided to go back to the official ATI linux driver, just so i can have the pretty effects enabled (lol).  So thanks for all the help, and hopefully ATI/AMD will release a fix for their retarded drivers. 

Here's my /etc/X11/xorg.conf file that seems to work with the open source ati driver ([_here's a very helpful page on how to install_]("https://help.ubuntu.com/community/RadeonDriver")), and it's stable and everything except for 3d rendering (including desktop effects) works.  

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

Section "Module"
# loaded automatically	Load "glx"
# loaded automatically	Load "dri"
	Load "drm"
EndSection

Section "Device"
	Identifier	"Radeon HD 2600XT"
	Driver		"ati"
	BusID		"PCI:05@00:00:0"
# not sure if needed	Option          "VideoOverlay" "on"
# not sure if needed	Option		"XAANoOffscreenPixmaps" "true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster 192N"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-85
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"SyncMaster 192N"
	Device		"Radeon HD 2600XT"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x870" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen	   "Default Screen"
EndSection

Section "ServerFlags"
# tried on and off, not completely sure what it does	
	Option "AIGLX" "Off"
EndSection

Section "DRI"
# not sure...something with Direct Rendering Mode obviously
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

---

### Post by beattyml1 on 2009-01-27
I tried the manual driver installation and it only made things worse, initially it made it so ubuntu would not startup normally but somehow I managed to fix that.  But still having trouble, I believed that I was able to get into ubuntu to test vlc and it still did not work, might it help to try this on a fresh install?

---

### Post by honkatonk on 2009-01-27
> **beattyml1 said:**
> I tried the manual driver installation and it only made things worse, initially it made it so ubuntu would not startup normally but somehow I managed to fix that.  But still having trouble, I believed that I was able to get into ubuntu to test vlc and it still did not work, might it help to try this on a fresh install?

wait, you mean a fresh Ubuntu install? It's gonna fix the problem that you have now, but you'll probably still have the original 3 problems. Do you know how you managed to fix the start up problem? Can you post xorg.conf from etc/X11/ , because that's probably where the problem is and people here might help you configure it properly.

---

### Post by beattyml1 on 2009-02-02
/etc/X11/xorg.config contents:

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

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

Right now my graphics card is disabled because enabling it messes up my computer

---

### Post by beattyml1 on 2009-03-03
Thanks to every one for their help but I decided just to get a better supported video card.  I ended up getting an nVidia GeForce 9500 GT and now everything works without a single problem.:D:D:D

---

