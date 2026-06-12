---
title: "Unreal tournament 2004 graphics issue"
date: 2008-02-09
forum: Gaming &amp; Leisure
---

### Post by ElTimo on 2008-02-09
Ok I have a strange problem with UT2004 (yes, I'm still playing it because my computer can't handle UT3).

Everything works fine, except for the fact that some of the textures on guns (specifically, the Redeemer) and the glows from lights and rockets, etc, and also the textures on the characters in cut scenes don't work. They are replaced with a white sort of pinstripe-looking texture. In short, I think that the game thinks they aren't there, and so it doesn't draw them. Other than that, the game works great. But this is just quite a large issue, as it makes the game look fugly. I have installed the latest patch and the megapack, so that's apparently not the issue. Any help at all would be appreciated. :confused:

EDIT: I actually think it's a problem with the particle effects, but I'm not sure. All I know is that the problem only occurs with OpenGL, not software rendering.

---

### Post by aknm on 2008-02-10
i have the same issue...my pc can handle UT3 though...but it looks like shreddies when an explosion happens infront of me, and the light texturing is also the same...plus the game seems to jolt quite a bit too, i think its the drivers, i have an nVidia 7300GT, i dont think it agrees too well with it somehow

---

### Post by FrozenFox on 2008-02-10
This is a well-known bug in the newest nvidia drivers. I have no idea why they released these drivers outside of beta mode in their obviously buggy condition. Revert to the older 100.x drivers, and things will work fine.

You may want to look into seeing if Envy can install an older driver if you're on Gutsy. I really don't know. If you're on hardy, there's no other way that worked for me than the following.

(There may be an easier (better, especially!) way on Gutsy, or even on Hardy, but I deal with stuff the manual way, waiting for solutions typically takes too long for my liking.  If you really want to try it, here's what I did..)

Actually, before I go on, NOTE that removing the drivers will probably "break" your system temporarily. If you remove the drivers, odds are you will be stuck temporarily at the command line next boot. You can always boot into the live cd for help. Also, doing it this way, which may be the only way unless you just want to deal with the texture issue until nvidia comes out with a fix (which may be a long time. shrug.), you need to install the video drivers again when you update an Xserver/xorg component or the linux kernel (if you are, all of this should be well-known knowledge below by now, lol). Anywho, if you want to try it this way..

What I did personally was:

1) go to the nvidia website, go to the drivers section, go to the driver archive, and download the driver version 100.14.19 to your desktop.
2) back up your xorg settings. start-->accessories-->terminal. type sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup  (note the lower/uppercase!)
3) in the console: sudo apt-get remove nvidia-glx-new (or it may be nvidia-glx, but i dont think so).
4) reboot. you will be stuck in command line most likely. if not, dont log in graphically, go to step 5.
5) press ctrl+alt+f2 or any one of the f keys that can get you to a command line login screen if youre not already at a command line or cmd login screen.
6) type cd /home/YOURNAME/Desktop
7) type ls and note the name of your NVIDIA driver. it will probably be NVIDIA-Linux-x86-100.14.19-pkg1.run
8 ) type sudo /etc/init.d/gdm stop
9) type ./NVIDIA-Linux-x86-100.14.19-pkg1.run  or whatever the name of the driver was. for short, you can probably get away with typing ./NVIDIA*
10) accept the installation stuff, its pretty robust, so dont worry about breaking the driver install. it may give some scary looking error, but its usually not a problem from my experience.
11) when it asks to update your xorg settings, say yes. if it doesnt ask, after this next step and youre stuck in command line, run sudo nvidia-xconfig then reboot
12) type sudo reboot. done, all should work well :)

If you have problems, you can essentially reverse the logic of the above steps and get back to your original system. Or you have a livecd. Etc, etc, etc.

---

### Post by davidkyn on 2008-02-10
I am using the standard Nvidia gxl from synaptic...Plays perfectly on my Note book with a geforce 8400M, 

Good to see linux playing some decent games these days...

---

### Post by Cresho on 2008-02-10
> **ElTimo said:**
> Ok I have a strange problem with UT2004 (yes, I'm still playing it because my computer can't handle UT3).

Everything works fine, except for the fact that some of the textures on guns (specifically, the Redeemer) and the glows from lights and rockets, etc, and also the textures on the characters in cut scenes don't work. They are replaced with a white sort of pinstripe-looking texture. In short, I think that the game thinks they aren't there, and so it doesn't draw them. Other than that, the game works great. But this is just quite a large issue, as it makes the game look fugly. I have installed the latest patch and the megapack, so that's apparently not the issue. Any help at all would be appreciated. :confused:

EDIT: I actually think it's a problem with the particle effects, but I'm not sure. All I know is that the problem only occurs with OpenGL, not software rendering.

How did you install the game?  wine or for native linux?

---

### Post by FrozenFox on 2008-02-11
[http://www.nvnews.net/vbulletin/showthread.php?t=106790](http://www.nvnews.net/vbulletin/showthread.php?t=106790)

If the pictures shown at the post this guy made on the forums nvidia has set up are similar to what you're experiencing, then it's indeed a problem with the 169.07/169.09 drivers you're having.. and reverting to the 100.x drivers works fine. It fixed the problem for me, anyway.

---

### Post by ElTimo on 2008-02-22
Installing the Ubuntu-restricted drivers did indeed fix the problem for me. I found this out myself, though, because I cant just post to a forum and wait around idly. ;-) Thanks for all your help though. That's my favorite part of the Linux community: (almost) everyone is willing to help (almost) everyone else. If the world worked more like Ubuntu...ok I'll shut up with the philosophical blahdy-blah now :-P

---

### Post by jjchico on 2008-04-22
In current hardy release candidates I had texture problems running UT2004. It was solved by:

1. Install nvidia-glx package (this will uninstall nvidia-glx-new)
2. Reboot your computer

Good luck.

---

### Post by Drezliok on 2008-04-22
> **jjchico said:**
> In current hardy release candidates I had texture problems running UT2004. It was solved by:

1. Install nvidia-glx package (this will uninstall nvidia-glx-new)
2. Reboot your computer

Good luck.

This does work, but With some help of others on the forum I got Nvidia's Beta Drivers working instead.

I can't wait for UT3 to have it's Linux client.

---

### Post by empthollow on 2008-04-26
I am running hardy and have this problem - just like the guys screenshots in the liked post.  i installed the nvidia-glx package and to tell you the truth i don't know if it fixed the problem because it created another problem with compiz.  No window borders.  I opted to go with the nvidia-glx-new package for now and hope for an update soon.  I would love to know of a fix for either problem though so that i can play my game normally.

---

### Post by FrozenFox on 2008-04-26
The window border problem has been posted about thousands of times in the last 2 years. Googling it will find your answer. adding ARGB visuals in xorg.conf is your most likely fix, if you come across a page telling you how.

    Option         "AddARGBGLXVisuals" "True"

is under my "Screen" section, but I'm not sure if it'll be the same for you. shrug. look it up

---

### Post by lovinlinux on 2008-04-26
i was having the same problems, so i reverted back to the 96.xx graphic drivers in envy and now everything seems to be working fine.

---

### Post by koyot on 2008-05-03
Hello,

1) How can I login as root in the console ?

2) Why the latest available drivers are still the 169.12, thouogh there seem to be a few more versions on the nvidia website : [http://www.nvidia.fr/object/linux_display_archive_fr.html]("http://www.nvidia.fr/object/linux_display_archive_fr.html") Are these versions not compatible with ubuntu ? Especialy the 173.08 one which seems to correct the problem with the textures under opengl ?

Thank you for you help, and excuse me for my poor english :-)

---

### Post by Perfect Storm on 2008-05-03
1)

```
[size=1]sudo <command>[/size]
```

executing a frontend gui with sudo;
```
[size=1]gksudo <command>[/size]
```

2)
In each Ubuntu development there will be a time where the freeze/stop newer software/lib/kernel etc. to test and iron out bugs. Unfortunatly Nvidia driver is close source so there are not much to do about it. You can install the the driver from Nvidia if you want or choose a rolling distro like Arch Linux.

---

### Post by empthollow on 2008-05-03
i ended up using nvidia-glx and editing the xorg.conf to have the
Option "AddARGBGLXVisuals" "True"
in it.  I put mine in the device section.  Thanks for the input.

---

### Post by HelpdeskSean on 2008-05-04
This doesn't excuse the bug or help for anything except UT2004, but if you disable "Coronas" in the graphics settings, the shreddies go away.  This was close enough to working for me to now wait for a packaged resolution.

--HDS

---

### Post by koyot on 2008-05-07
unfortunately the coronas setting doesn't change anything, and I can't manage to install a former version of the drivers, i just have to wait a packaged update coming from ubuntu or from envyng...

---

### Post by HelpdeskSean on 2008-05-11
You're right.  Taking off coronas fixes the shreddies on the lights, but not the ones on the explosions or gunfire effects.  Its still much more playable with them off, but I do hope Nvidia resolves the problem eventually.

---

### Post by koyot on 2008-06-09
thanks anyway for the coronas off tip, it reduces the effects of the bug

these days, there were already several updates including some nvidia packages, but the bug is still there, did I miss something ?

---

### Post by Sleaka J on 2008-06-13
Is this bug fixed in the 173.14.05 drivers? Cause I'll play UT2004 in Windows until this is fixed.

---

### Post by koyot on 2008-06-19
YES, the 173.14.05 drivers do solve this bug ! in addition, I managed to install them the easy way using Envy NG, they are at last available in there :-)

---

### Post by abhiroopb on 2009-09-15
A year on and I still love this game!!

Unfortunately, I am having this same issue. I have played UT2004 on this computer on older versions of Ubuntu (using the linux installer) and never had a problem.

My nVidia driver version is: 180.44 (standard one that can be found when ubuntu is first installed).

---

### Post by abhiroopb on 2009-09-15
my xorg.conf

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "SAMSUNG LCD"
	HorizSync       30.0 - 81.0
	VertRefresh     56.0 - 75.0
	Option         "DPMS"
	# HorizSync source: edid, VertRefresh source: edid
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	DefaultDepth    24
	Option         "TwinView" "1"
	Option         "TwinViewXineramaInfoOrder" "CRT-0"
	Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1440+0 ; CRT: 1440x900+0+0,NULL"
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "dbe"
	Load           "extmod"
	Load           "type1"
	Load           "freetype"
	Load           "glx"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
	# generated from default
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Device0"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
	BoardName      "GeForce Go 7400"
EndSection

Section "ServerFlags"
	Option         "Xinerama" "0"
	Option	"DontZap"	"False"
EndSection

```

---

