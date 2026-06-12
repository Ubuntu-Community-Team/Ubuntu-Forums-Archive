---
title: "No Title Bar in Compiz Fusion"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by Sk1ppy on 2007-08-28
So recently tried to install Compiz-Fusion.  I used [this]("http://ubuntuforums.org/showthread.php?t=536149") method to install it but when I run Compiz my title bars disappear. Also, when i go into the Emerald Themer and try to change theme, see if it helps anything, nothing changes when I click a theme. I can see to find the answer to this particular problem. If anyone needs any info to assess the situation I'd be happy to provide it.

---

### Post by ittiam on 2007-08-28
Output for

```
glxinfo | grep direct rendering
```

If it says yes, you are well and good. And also I hope you got appropriate drivers for your video card.

After this, problem might be with your window manager. Check your window manager setting, I also had this problem sometimes when I start compiz. I switch my window manager to metacity and back to compiz it starts running again perfectly.

---

### Post by psyopper on 2007-08-29
Can I take a stab in the dark and guess you are using an Nvidia video card? Further, I'm going to continue to guess that you are missing the following line in your xorg.conf:
```
 Option         "AddARGBGLXVisuals" "True"
```

Of course this will be the one time where you aren't running an nvidia card, or you are and do have the above line... By the way, that line should be in the "Device" section with the other Options.

Let us know if this resolves it!

---

### Post by michael37 on 2007-08-29
> **ittiam said:**
> Output for

```
glxinfo | grep direct rendering
```

If it says yes, you are well and good. And also I hope you got appropriate drivers for your video card.

After this, problem might be with your window manager. Check your window manager setting, I also had this problem sometimes when I start compiz. I switch my window manager to metacity and back to compiz it starts running again perfectly.

First of all, the command quoted above is incorrect.  It should be 

```
glxinfo | grep direct
```

Second, if that commands reports "no", it's no reason to panic.  I have it set to No, and it a perfectly valid configuration with Xgl.

Lastly, please tell us which video card you are using.  Nvidia, ATI, Intel?

---

### Post by ittiam on 2007-08-29
> **michael37 said:**
> First of all, the command quoted above is incorrect.  It should be 

```
glxinfo | grep direct
```

Second, if that commands reports "no", it's no reason to panic.  I have it set to No, and it a perfectly valid configuration with Xgl.

Lastly, please tell us which video card you are using.  Nvidia, ATI, Intel?

Sorry missed the quotes in the command. It is glxinfo | grep "direct rendering". And i did not know that without direct rendering enabled you cud have compiz fusion running. I use AIGLX thought

---

### Post by michael37 on 2007-08-29
> **ittiam said:**
> Sorry missed the quotes in the command. It is glxinfo | grep "direct rendering". And i did not know that without direct rendering enabled you cud have compiz fusion running. I use AIGLX thought

I have an ATI video card and I use fglrx driver.   This driver uses funky extension ATIFGLRXDRI instead of XFree86-DRI, so I end up with in my glxinfo output.

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No

Again, it all depends on a driver and the xorg configuration.

---

### Post by amer1337 on 2007-10-12
im  having this issue too, wher ein my xorg do i put  Option         "AddARGBGLXVisuals" "True" 

? an example would help :)

---

### Post by michael37 on 2007-10-12
> **amer1337 said:**
> im  having this issue too, wher ein my xorg do i put  Option         "AddARGBGLXVisuals" "True" 

? an example would help :)

In Device section.  But this option is ONLY for Nvidia graphics and ONLY for Nvidia binary driver.

```

Section "Device"
Identifier "nVidia Corporation GeForce 6200 A-LE"
Driver "nvidia"
Option "RenderAccel" "true"
Option "Allow GLXWithCompostite"
Option "AddARGBGLXVisuals" "True"
EndSection

```

---

### Post by Forlong on 2007-10-12
If you have the proprietary (restricted) nvidia driver installed, all you have to do is run this command:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
it takes care of everything for you.

---

### Post by bootsbradford on 2007-10-15
I am having exactly the same problem - no title bar. I have upgraded to gutsy and am using compiz fusion. I have an ATI Radeon X600 video card.

Any ideas what I need to do?

---

### Post by bootsbradford on 2007-10-15
Not quite sure how, but I now have Emerald working as the Window Manager.

However, I cannot move or resize windows at the moment? What should I do to enable this?

---

### Post by bootsbradford on 2007-10-15
D'oh! I hadn't enabled the 'move' or 'resize' plugin...

---

### Post by Peacepunk on 2007-10-17
I heve the same on an intel chipset with the i810 driver. It's erratic & I have to restart either "enable desktop effect" or fiddle around with the gnome-compiz-manager. The killing thing is each time I reboot from a compiz-enabled desktop, I end up without titlebar.

Any hints regarding i810/inter chipset ?
I run compiz 0.3.6 - not fusiion, as it seems.

Cheers

---

### Post by HokeyFry on 2007-10-17
have any of you tried pressing "alt + F2", then running "emerald --replace"? that is what fixes it for me if that happens

---

### Post by michael37 on 2007-10-17
> **Peacepunk said:**
> I heve the same on an intel chipset with the i810 driver. It's erratic & I have to restart either "enable desktop effect" or fiddle around with the gnome-compiz-manager. The killing thing is each time I reboot from a compiz-enabled desktop, I end up without titlebar.

Any hints regarding i810/inter chipset ?
I run compiz 0.3.6 - not fusiion, as it seems.

Cheers

I would strongly recommending upgrading compiz to version 0.5.x or 0.6.x (the latter is for Gutsy only).  Old compiz is not only buggy but also no longer supported.

---

### Post by DOH on 2007-10-17
Forlong's suggestion above worked for me.   Compiz runs smooth now....Just need to figure out how to get the cube working.

---

### Post by bromix on 2007-10-17
In compiz configuration....switch your horizontal size to 4...  then enable Desktop Cube and Rotate Cube.

---

### Post by aliencam on 2007-10-17
I have had the same problem, however I have a title bar for awhile, then it goes away while I am using "mouse rotate" to rotate the cube.  I'm on an ATI Radeon 9800 pro without the restricted drivers, and just removed emerald to try to fix it.  


did anyone else notice that emerald is no longer in the "add/remove", it is only in synaptic... 

t came back for me randomly while I was messing with the advanced desktop settings manager, but next time I will try alt-f2 and emerald --replace  like hokeyfry suggested...

---

### Post by Peacepunk on 2007-10-18
@ Michael: OUch, I wasn't aware I was so outdated...
@ Bromix & DOH: Nothing prevents you from having a 3-faced Cube, or 5 or whatever - In Beryl at least; proved, tested.
@ All: As of Now, I disabled Metacity in Compiz-manager, seems to do the trick but as it's erratic, who knows... Rebooted 3 times since, that doesn't prove nothing...

Cheers

---

### Post by waza456 on 2007-10-18
hi everyone. i have an ati radeon x1300 card whith fglrx driver, i just upgraded to gutsy and enabled desktop effects, and all titlebars disappeared.
i tried adding the " Option         "AddARGBGLXVisuals" "True""  line to my xorg.conf, but it didn't work.
I type glxifo |grep direct and what i get is this:
:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

my xorg.conf can be found here [http://pastebin.ca/741829](http://pastebin.ca/741829)
the device section is this:
> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Option "AddARGBGLXVisuals" "True"
EndSection



any ideas?

---

### Post by BenTheBear on 2007-10-18
i too share this problem but i have intel intergrated card. pls pls sum1 have a solution, im constantly trying to sort this out but feel like ive hit a brick wall

---

### Post by DavidTangye on 2007-10-18
> **DOH said:**
> Forlong's suggestion above worked for me.   Compiz runs smooth now....Just need to figure out how to get the cube working.
In compiz configuration....switch your horizontal size to 4...  then enable Desktop Cube and Rotate Cube.

---

### Post by cajunlibra on 2007-10-18
I'm having the same problem.  I have the ATI Mobility FireGL V3100 using fglrx


root@cajun:/home/cajun# fglrxinfo
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: unable to open display :0
root@cajun:/home/cajun# glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
root@cajun:/home/cajun#


xorg.conf:
Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	Busid		"PCI:1:0:0"
EndSection

I have not been able to get compiz to work properly for longer than an hour.

When I start the Compiz Configuration Manager, I always get this dbus error:"  Dbus failed to load. The dbus plugin appears to not be active. Some options maybe missing without the dbus plugin. Would you like to enable it? "  I click "Yes Activate" and then I can make changes but it doesn't stick.

---

### Post by michael37 on 2007-10-19
> **cajunlibra said:**
> I'm having the same problem.  I have the ATI Mobility FireGL V3100 using fglrx


root@cajun:/home/cajun# fglrxinfo
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Error: unable to open display :0
root@cajun:/home/cajun# glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
root@cajun:/home/cajun#


xorg.conf:
Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	Busid		"PCI:1:0:0"
EndSection

I have not been able to get compiz to work properly for longer than an hour.

When I start the Compiz Configuration Manager, I always get this dbus error:"  Dbus failed to load. The dbus plugin appears to not be active. Some options maybe missing without the dbus plugin. Would you like to enable it? "  I click "Yes Activate" and then I can make changes but it doesn't stick.

Try troubleshooting in [thread=537836]this thread[/thread].

---

### Post by Forlong on 2007-10-19
waza456, first of all, that option is for Nvidia users only.

Your problem are not the titlebars but Compiz isn't running at all.
```
Section "Extensions"

        Option    "Composite"       "1"

EndSection
```
This has to be set to "0" with the fglrx driver!

You also need to install Xgl:
```
sudo apt-get install xserver-xgl
```

---

### Post by waza456 on 2007-10-19
well, i removed the Option "AddARGBGLXVisuals" "True" since it's only for nvidia cards. I also changed the Option Composite from 1 to 0. I pressed alt+ctrl+backspace, but nothing changed. I still have the same problem.
@ forlong: you said that my problem is not the titlebars, but that compiz isn't running at all. Why do you think that? I mean, everything else works just fine, including the cube, rotating the cube and everything else. I just can't get my titlebars to appear. Or, so i think at least.
@ all: if you have an ati card and you have gutsy with compiz enabled, and everything is fine, could you post your xorg.conf, to figure out what the problem is with mine?
thanks

---

### Post by Forlong on 2007-10-19
> **waza456 said:**
> everything else works just fine, including the cube, rotating the cube and everything else. I just can't get my titlebars to appear.
Oh, I would have never guessed that, because that option in your xorg.conf is usually fatal.

Is the Window Decoration plugin in ccsm enabled?

---

### Post by waza456 on 2007-10-19
> **Forlong said:**
> Oh, I would have never guessed that, because that option in your xorg.conf is usually fatal.

Is the Window Decoration plugin in ccsm enabled?

yes, it' s enabled all right. but i've tried enabling and disabling it several times. I see no difference.

---

### Post by waza456 on 2007-10-19
@forlong: i used the info in your blog([http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)) and fixed it! I installed emerald, and then i set emerald in the ccsm>window decoration>command. And now it works! thanks a lot.

---

### Post by cajunlibra on 2007-10-23
> **michael37 said:**
> Try troubleshooting in [thread=537836]this thread[/thread].

That thread specifically says that it isn't advised for troubleshooting Gutsy which I have.

---

### Post by michael37 on 2007-10-23
> **cajunlibra said:**
> That thread specifically says that it isn't advised for troubleshooting Gutsy which I have.

Indeed, I started new [thread=569654]Gutsy thread for ATI video card owners[/thread].  Begin with HOWTOs on the first page.  Good luck!

---

### Post by michael37 on 2007-10-23
> **Forlong said:**
> waza456, first of all, that option is for Nvidia users only.

Your problem are not the titlebars but Compiz isn't running at all.
```
Section "Extensions"

        Option    "Composite"       "1"

EndSection
```
This has to be set to "0" with the fglrx driver!

You also need to install Xgl:
```
sudo apt-get install xserver-xgl
```

Forlong, just for the record, I am running ATI fglrx driver with Xgl and Compiz and Composite=1, and Xorg.0.log says that Composite is enabled.  Looks like an oddball change in Gutsy.  Doesn't seem to hurt anything nor help anything since all primary rendering is done on display :1 which is under complete Xgl control.

---

### Post by HXn on 2007-10-23
Having the same problem with NVIDIA GeForce4 Ti4400.

```
$ glxinfo | grep direct
direct rendering: Yes
```

Added the following under "Devices":
```
Option         "AddARGBGLXVisuals" "True"
```

Tried this:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

Which adds the "AddARGBGLXVisuals" line to "Screen" instead of "Devices"

Still no title bar.  Installed compizfusion-settings-manager and everything else seems to be working fine.  Any ideas?

---

### Post by cinnamonjames on 2007-10-24
Hi, I had this same problem with Gutsy on nVidia proprietary drivers.  I googled high and low and evetually found this blog [http://craig.dubculture.co.nz/blog/2007/09/23/no-window-decorators-in-compiz-in-ubuntu-gutsy/](http://craig.dubculture.co.nz/blog/2007/09/23/no-window-decorators-in-compiz-in-ubuntu-gutsy/)

I c&p'ed his code into a terminal, reloaded the window manager (using the Emerald icon in my taskbar) and I have title bars again!

I haven't rebooted since, but they are here now, and I'm happy =')

---

### Post by HXn on 2007-10-24
I installed Emerald which brought the title bar, etc. back.

```
sudo apt-get install emerald
```

---

### Post by siddharth.dawara on 2007-10-25
I had the same problem

I killed emerald

Installed this.

sudo apt-get install xserver-xgl

Applied this line of code.

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

Enabled the "Place Windows" plugin apparently this has something to do with fixing the problem.

Restarted emerald from the command line. It still gives me the weird error prompt when I run it though. But I have titlebars.

---

### Post by forumkiller on 2007-12-11
> **siddharth.dawara said:**
> I had the same problem

I killed emerald

Installed this.

sudo apt-get install xserver-xgl

Applied this line of code.

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

Enabled the "Place Windows" plugin apparently this has something to do with fixing the problem.

Restarted emerald from the command line. It still gives me the weird error prompt when I run it though. But I have titlebars.

im quite a new user to ubuntu and stopped using it because of these problems. Now the effects are too good to do without, so i gotta fix it.

I tried the sudo nvidia-xconfig --add-argh-glx-visuals -d 24 as u suggest above, and it did somehting, yet didn't fix my title bars. I didn't try the install because i didn't want to try installing stuff i dont no until someone has told me personally to do it.

I did type this in after pressing CTRL+ALT+F1 as my terminal is currently not working now.

And because there have been so many suggestions in this thread i have no idea what code im supposed to input to fix this, and it doesn't sound smart just to type them all in not knowing what they actually do.

So can someone just give me a straight solution and explain to me exactly how to do it. As its been very difficult to grasp linux when everyone is talking like they are speaking to other people who have already grasped it, as i have only learned from me, and all i know is 13 years of Windows, some DOS code and Mac OSX Tiger/Leopard Experience.

---

### Post by forumkiller on 2007-12-12
> **forumkiller said:**
> im quite a new user to ubuntu and stopped using it because of these problems. Now the effects are too good to do without, so i gotta fix it.

I tried the sudo nvidia-xconfig --add-argh-glx-visuals -d 24 as u suggest above, and it did somehting, yet didn't fix my title bars. I didn't try the install because i didn't want to try installing stuff i dont no until someone has told me personally to do it.

I did type this in after pressing CTRL+ALT+F1 as my terminal is currently not working now.

And because there have been so many suggestions in this thread i have no idea what code im supposed to input to fix this, and it doesn't sound smart just to type them all in not knowing what they actually do.

So can someone just give me a straight solution and explain to me exactly how to do it. As its been very difficult to grasp linux when everyone is talking like they are speaking to other people who have already grasped it, as i have only learned from me, and all i know is 13 years of Windows, some DOS code and Mac OSX Tiger/Leopard Experience.

OK heres the weird thing, i start up ubuntu today and its the wrong resolution, its using 1600x1200 which is what my previous monitor was using. So i changed it to the 1280x768 like i had before and nothing happend. So i restarted, and when it started up the title bar had returned and i still had the desktop effects. :O Whats it all about lol :)

So im not ever changing a setting ever again in case i wreck this. :D

---

### Post by jgalt on 2008-02-10
> **psyopper said:**
> Can I take a stab in the dark and guess you are using an Nvidia video card? Further, I'm going to continue to guess that you are missing the following line in your xorg.conf:
```
 Option         "AddARGBGLXVisuals" "True"
```

Of course this will be the one time where you aren't running an nvidia card, or you are and do have the above line... By the way, that line should be in the "Device" section with the other Options.

Let us know if this resolves it!

This is exactly my problem and I am running a Nvidia card. However this didn't fix my problem. I'm using the AMD chipset with the Gutsy 7.10-x64 kde. How do I fix this? I've installed the drivers. I'm completely new to linux so I could use the help. Of course now that I think about it my problem may be that I don't know how to access xorg.conf to make the correction. Thanks.

---

### Post by BassKozz on 2008-02-19
I am having the same issues as everyone else here, no "title bars" on the windows, But what makes my situation unique is that I am using a Dual-Display Setup, and each display is it's own X Session, and wouldn't you know it the primary Monitor/Screen works flawlessly;
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/th_wtitlebars.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/wtitlebars.jpg)
[size=1]*(Click to see larger)*[/size]

 but the secondary monitor doesn't :(;
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/th_notitlebars.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/notitlebars.jpg)
[size=1]*(Click to see larger)*[/size]
It's missing the "title bars" on the windows and when I click on the shutdown/power button (top right) the whole system freezes.

I've tried the various suggestions posted in this thread, here is what my *xorg.conf* file looks like:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Fri Jan 11 14:26:48 PST 2008

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Fri Jan 11 14:27:25 PST 2008
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

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HSD HG216"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8600 GT]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    Option         "AddARGBGLXVisuals" "True"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    Option         "AddARGBGLXVisuals" "True"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Modes      "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1280x1024 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```
What can I do here to get "title bars" back on my windows on my secondary display?
TIA

**_[SOLVED]_** [size=1][thanks to ArchangHell]("http://ubuntuforums.org/showthread.php?p=4365883#post4365883")[/size]... 
I went to System->Preferences->Appearance and change the *Visual Effects* to **NONE**, the problem goes away, meaning Window Title Bar's show up in both Display's...
I then went back and changed *Visual Effects* to **Normal** and it's still works, :D it's fixed... (for now) [-o<
So this confirms it's a Compiz issue, now to find out what/why it's behaving this way :confused:

---

### Post by diabzero on 2008-03-16
I have tried pretty much EVERYTHING to fix this problem.  I finally got it to work with this guy's answer =)

THANKS!

> **Forlong said:**
> If you have the proprietary (restricted) nvidia driver installed, all you have to do is run this command:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
it takes care of everything for you.

---

### Post by nichpakaich on 2008-03-22
I tried to disable the GUI Animation under Style, it worked just fine (don't ask how much time I've spent on the net to figure how to deal with the previous problem)

---

### Post by mplexus on 2008-03-30
> **psyopper said:**
> Can I take a stab in the dark and guess you are using an Nvidia video card? Further, I'm going to continue to guess that you are missing the following line in your xorg.conf:
```
 Option         "AddARGBGLXVisuals" "True"
```

Of course this will be the one time where you aren't running an nvidia card, or you are and do have the above line... By the way, that line should be in the "Device" section with the other Options.

Let us know if this resolves it!

It sure resolved the problem for me! (nvidia Go 5700) Many thanks!

---

### Post by noirtier_de_villefort on 2008-04-02
perfection... using "sudo nvidia-xconfig --add-argb-glx-visuals -d 24" solved *all* of my compiz problems... white windows and such... thanks Forlong

---

### Post by morphmatrix on 2008-06-22
also have the same issue, i always reload the windows manager to get my title bar back, but then i tried adding compiz under startup programs which resoved permanently my problem.  now my computer starts up with title bars :) hope this would help.

---

