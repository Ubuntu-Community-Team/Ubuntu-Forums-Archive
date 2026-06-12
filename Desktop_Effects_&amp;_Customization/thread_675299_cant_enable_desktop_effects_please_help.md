---
title: "cant enable desktop effects please help"
date: 2008-01-22
forum: Desktop Effects &amp; Customization
---

### Post by zuknivek on 2008-01-22
I have recently installed ubuntu on my old Compaq Presario 5000. It has an integrated video card and i'm not sure if i need video card drivers to get my desktop effects to work. When i try to enable the desktop effects it says "cannot enable desktop effects." There are no details about why i cant but it would be greatly appreciated if someone could tell me how to enable desktop effects.

---

### Post by melopsittacus on 2008-01-22
Hi Zuknivek! That may be exactly what you need. I could enable desktop effects only after installing video drivers. What kind of video card are you using?

---

### Post by zuknivek on 2008-01-22
My video card is built in with my motherboard and my motherboard is a foxconn. I'm not sure if this helps but i've searched the internet for about an hour trying to find drivers for my video card and i cant seem to find any. any tips?

---

### Post by zuknivek on 2008-01-24
I found out what video card i have. Its not foxconn or whatever i said before. Instead it is an intel Integrated video card. Does anybody know where i can find drivers for such a device?

---

### Post by zuknivek on 2008-01-25
anybody?

---

### Post by Ub1476 on 2008-01-25
Post the output of this:

```
lspci | grep VGA

compiz
```

---

### Post by zuknivek on 2008-01-25
[IMG]http://i186.photobucket.com/albums/x303/kevinkuz2009/Screenshot-kevincomcraps.png[/IMG]
thats what happened when i typed in those commands.

---

### Post by rosegarden78 on 2008-01-25
Follow the instructions I posted [here]("http://ubuntuforums.org/showthread.php?t=677959") but they only work if you start with Ubuntu GG 7.10 fresh install before adding KDE or XFCE.  You can also get a Mac-style dock [here]("http://ubuntuforums.org/showthread.php?t=385981").

---

### Post by zuknivek on 2008-01-25
I tried your instructions and they did not help. I am not able to enable desktop effects still.

---

### Post by zuknivek on 2008-01-25
I still cant find out how to enable my desktop effects. Is it possible that my graphics card sucks so bad that it can't run desktop effects? That might be the problem because my graphics card only has 32mb of on board memory.

---

### Post by widowmaker on 2008-01-26
zuknivek,

From what I have been experiencing is that if you don't have at least a 128 mb card your S.O.L. The bigger the better. Check the Ubuntu site for specs on running all the desktop effects and Beryl etc etc. I did have Beryl running on one of my desktops with a 64 mb card, but it was jumpy and doggy to say the least.

Widowmaker

---

### Post by xeth_delta on 2008-01-26
In the past I managed to get beryl (now compiz-fusion) working on a laptop with a slow card that used only 32MB of video memory.

zuknivek, please post the output of:

```
sudo lshw -C Video
```
and
```
glxinfo | grep -i direct
```

---

### Post by rosegarden78 on 2008-01-26
> **zuknivek said:**
> I tried your instructions and they did not help. I am not able to enable desktop effects still.

Well my mother's old Dell Dimension is having problems with compiz as well but I tried it on a Kubuntu system.  My Intel 915 wasn't fully supported until Gutsy.  Ubuntu Gutsy comes with basic eye candy pre-installed.  The other  compiz packages especially the settings manager give you more features.  I'm sorry I cannot offer more technical assistance.

---

### Post by zuknivek on 2008-01-26
bump

---

### Post by zuknivek on 2008-01-26
> **xeth_delta said:**
> In the past I managed to get beryl (now compiz-fusion) working on a laptop with a slow card that used only 32MB of video memory.

zuknivek, please post the output of:

```
sudo lshw -C Video
```
and
```
glxinfo | grep -i direct
```

[IMG]http://i186.photobucket.com/albums/x303/kevinkuz2009/Screenshot-kevincomcraps-1.png[/IMG]

---

### Post by zuknivek on 2008-01-26
> **widowmaker said:**
> zuknivek,

From what I have been experiencing is that if you don't have at least a 128 mb card your S.O.L. The bigger the better. Check the Ubuntu site for specs on running all the desktop effects and Beryl etc etc. I did have Beryl running on one of my desktops with a 64 mb card, but it was jumpy and doggy to say the least.

Widowmaker

Is there a way to tell if i have drivers already installed? I might already have drivers installed but my video card is so crappy i cant run desktop effects.

---

### Post by xeth_delta on 2008-01-26
zuknivek, from the output you offered I can see that 3D acceleration is not enabled. I do believe you will be able to run 3D effects, if you have enough memory. Do you have at least 32 MB dedicated to the graphics card?

Please post the contents of the file "/etc/X11/xorg.conf". Do not take a picture of it, open it:
```
gedit /etc/X11/xorg.conf
```
and then copy the contents and paste it in your post. Please place the contents between code tags (use the button with "#" in the posting window).

It seems your drivers are not configured properly.

---

### Post by zuknivek on 2008-01-26
> **xeth_delta said:**
> zuknivek, from the output you offered I can see that 3D acceleration is not enabled. I do believe you will be able to run 3D effects, if you have enough memory. Do you have at least 32 MB dedicated to the graphics card?

Please post the contents of the file "/etc/X11/xorg.conf". Do not take a picture of it, open it:
```
gedit /etc/X11/xorg.conf
```
and then copy the contents and paste it in your post. Please place the contents between code tags (use the button with "#" in the posting window).

It seems your drivers are not configured properly.

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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

Hopefully this is what you requested. When i typed in what you said this popped up in a new window.

---

### Post by Beholder87 on 2008-01-26
hi I am having the same problems here....
I just installed my ubuntu 7.10 (gutsy) and it seems that my video is a little slow... (and i can't enable desktop effects)

i think that my video-card is ok, i used to play warcraft III: TFT (Dota-Allstars) when i was using windows and the video was good. i never had problems playing games....

my graphics card is a **Intel 945G** integrated graphics controller

I attached my configs:


 lspci | grep VGA
compiz

gedit /etc/x11/xorg.conf

 sudo lshw -C Video


someone could help me please? 
thanks

---

### Post by zuknivek on 2008-01-26
> **Beholder87 said:**
> hi I am having the same problems here....
I just installed my ubuntu 7.10 (gutsy) and it seems that my video is a little slow... (and i can't enable desktop effects)

i think that my video-card is ok, i used to play warcraft III: TFT (Dota-Allstars) when i was using windows and the video was good. i never had problems playing games....

my graphics card is a **Intel 945G** integrated graphics controller

I attached my configs:


 lspci | grep VGA
compiz

gedit /etc/x11/xorg.conf

 sudo lshw -C Video


someone could help me please? 
thanks

glad to know someone else has this problem and its not just my lack of knowledge about Ubuntu

---

### Post by xeth_delta on 2008-01-27
zuknivek, make a back-up of /etc/X11/xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bkp
```
Now, in the <<Section "Module">>, change from
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection
```
to
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
#	Load	"vbe"
	Load	"dbe"
EndSection
```

Section "Device", change from:
```
Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
EndSection
```
to
```
Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
	Option      	"DRI"     "true"
EndSection
```

Section "ServerLayout"

change from
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```
to
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	Option             "AIGLX" 	"true"
EndSection
```

Restart the X server (Control Alt Backspace), log-in again and type"
```
glxinfo | grep -i direct
```
What is the output?

---

### Post by xeth_delta on 2008-01-27
> **Beholder87 said:**
> hi I am having the same problems here....
I just installed my ubuntu 7.10 (gutsy) and it seems that my video is a little slow... (and i can't enable desktop effects)

i think that my video-card is ok, i used to play warcraft III: TFT (Dota-Allstars) when i was using windows and the video was good. i never had problems playing games....

my graphics card is a **Intel 945G** integrated graphics controller

I attached my configs:


 lspci | grep VGA
compiz

gedit /etc/x11/xorg.conf

 sudo lshw -C Video


someone could help me please? 
thanks

Welcome to the forums! Your problem is that you don't have direct acceleration enabled on your computer. By looking in your /etc/X11/xorg.conf, you will notice the following:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection
```

You are using the generic vesa driver, which does not have hardware acceleration. My recommendation would be first making a back-up of the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bkp[CODE]
and then run
[CODE]sudo dpkg-reconfigure xserver-xorg
```
Follow the instructions, and hopefully you will have a new xorg.conf file with the corresct driver listed. Restart the X11 server with Control-Alt-Backspace and log-in again.
Type
```
glxinfo | grep -i direct
```
and post the output. I suspect that after having hardware acceleration compiz should work.
Let us know how it goes.

---

### Post by Beholder87 on 2008-01-27
> I suspect that after having hardware acceleration compiz should work.
Let us know how it goes.

Good Shoot!!!!!!

thanks dude! now when i try to change the visual effects, it doesn't show me the error message again! 

but my video is a little slow, i think that i'll use no effects and buy a nvidia card as soon as possible.

=)

:)

---

### Post by xeth_delta on 2008-01-27
> **Beholder87 said:**
> Good Shoot!!!!!!

thanks dude! now when i try to change the visual effects, it doesn't show me the error message again! 

but my video is a little slow, i think that i'll use no effects and buy a nvidia card as soon as possible.

=)

:)

You are most welcome. My laptop has an i945GM card and runs actually smoothly at the screen native resolution, 1280*800 that is. What resolution are you using?

Can you check that you do have hardware acceleration? "glxinfo | grep direct"

---

### Post by Beholder87 on 2008-01-28
> **xeth_delta said:**
> 
Can you check that you do have hardware acceleration? "glxinfo | grep direct"

```

monster@monster:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
monster@monster:~$ 

```

i use here 1024 X 768 85 Hz.... when i was using windows it was set to 75 Hz....
**problably hardware acceleration would help to solve the problem can you help me?**

i logged into windows and i got the video configuration:
```

	Intel(R) Graphics Media Accelerator Driver Report


Report Date:		01/28/2008
Report Time[hr:mm:ss]:	12:36:21
Driver Version:		7.14.10.1350
Operating System:		Windows Vista (TM) Home Basic* ,  (6.0.6000)
Default Language:		English
DirectX* Version:		10.0
Physical Memory:		1524 MB
Minimum Graphics Memory:	8 MB
Maximum Graphics Memory:	256 MB
Graphics Memory in Use:	67 MB
Processor:		x86
Processor Speed:		3191 MHZ
Vendor ID:		8086
Device ID:		2772
Device Revision:		02


*   Accelerator Information   *

Accelerator in Use:		Intel(R) 82945G Express Chipset Family
Video BIOS:		1295
Current Graphics Mode:	1024 by 768 True Color (75 Hz)



*   Devices Connected to the Graphics Accelerator   *


Active Monitors: 1


*   Monitor   *

Monitor Name:		Dell P780
Display Type:		Analog
Gamma Value:		2.50
DDC2 Protocol:		Supported
Maximum Image Size:	Horizontal: 12.0  inches
			Vertical:   9.0  inches
Monitor Supported Modes:
640 by 480 (60 Hz)
640 by 480 (75 Hz)
640 by 480 (85 Hz)
720 by 400 (70 Hz)
800 by 600 (75 Hz)
800 by 600 (85 Hz)
1024 by 768 (75 Hz)
1024 by 768 (85 Hz)
1280 by 1024 (75 Hz)
1600 by 1200 (60 Hz)
Display Power Management Support:
	Standby Mode:	Not Supported
	Suspend Mode:	Not Supported
	Active Off Mode: Supported
Raw EDID:
00 ff ff ff ff ff ff 00 10 ac 0f 51 57 38 30 31
1c 0b 01 02 0e 21 18 96 2b 0c c9 a0 57 47 9b 27
12 48 4c a4 43 00 61 59 45 59 a9 40 31 59 01 01
01 01 01 01 01 01 c3 1e 00 20 41 00 20 30 10 60
13 00 38 ea 10 00 00 1e 00 00 00 ff 00 37 35 55
58 52 31 37 39 31 30 38 57 0a 00 00 00 fc 00 44
45 4c 4c 20 50 37 38 30 0a 20 20 20 00 00 00 fd
00 30 78 1e 55 ff 00 0a 20 20 20 20 20 20 00 b2

* Other names and brands are the property of their respective owners.

```

you may compare it to the /etc/X11/xorg.conf:
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"	
EndSection

Section "Monitor"
	Identifier	"DELL P780"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82945G/GZ Integrated Graphics Controller"
	Monitor		"DELL P780"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Hardware Acceleration? Help please =) thanks

---

### Post by Therion on 2008-01-28
Just a wild thought AND, most likely, a long shot but I'll throw it out there.  

Could these issues be related to menu.lst and the "noapic/nolapic" options being disabled?

Modify the display settings to 16-bit color depth??


/grasping at straws...

---

### Post by zuknivek on 2008-01-28
> **xeth_delta said:**
> zuknivek, make a back-up of /etc/X11/xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bkp
```
Now, in the <<Section "Module">>, change from
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection
```
to
```
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
#	Load	"vbe"
	Load	"dbe"
EndSection
```

Section "Device", change from:
```
Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
EndSection
```
to
```
Section "Device"
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
	Option      	"DRI"     "true"
EndSection
```

Section "ServerLayout"

change from
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```
to
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	Option             "AIGLX" 	"true"
EndSection
```

Restart the X server (Control Alt Backspace), log-in again and type"
```
glxinfo | grep -i direct
```
What is the output?

i did everything you said to do except i couldn't copy the file to the X11 folder because i didn't have permissions to. So i dont know what to do.

---

### Post by xeth_delta on 2008-01-29
> **zuknivek said:**
> i did everything you said to do except i couldn't copy the file to the X11 folder because i didn't have permissions to. So i dont know what to do.

You have to open the file with root/administrative privileges, for example:
```
sudo nano /etc/X11/xorg.conf
```
or if you use Gnome
```
gksudo gedit /etc/X11/xorg.conf
```
or for KDE
```
kdesu kate /etc/X11/xorg.conf
```

---

### Post by zuknivek on 2008-01-29
> **xeth_delta said:**
> You have to open the file with root/administrative privileges, for example:
```
sudo nano /etc/X11/xorg.conf
```
or if you use Gnome
```
gksudo gedit /etc/X11/xorg.conf
```
or for KDE
```
kdesu kate /etc/X11/xorg.conf
```

Ok i did what you said and it worked. I changed everything you said and when i type in ```
glxinfo | grep -i direct
```
i get this answer
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```
I appreciate all the help you are giving me. Thank you.

---

### Post by xeth_delta on 2008-01-29
> **zuknivek said:**
> Ok i did what you said and it worked. I changed everything you said and when i type in ```
glxinfo | grep -i direct
```
i get this answer
```
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

```
I appreciate all the help you are giving me. Thank you.

You're welcome!  Have you tried to reconfigure?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dark_harmonics on 2008-01-29
I have had so many video problems in the past. Your issues are definately a result of not having direct rendering on. I agree with the above posters that you should backup your xorg.conf file

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
and then try a reconfigure with
sudo dpkg-reconfigure xserver-xorg
Try the detect option and if that fails maybe point it towards your intel drivers (i810 driver). If this prevents your X windows from starting you may need to replace your xorg.conf with the backup you made at a command prompt and then type: sudo /etc/init.d/gdm restart

---

### Post by dark_harmonics on 2008-01-29
> **Beholder87 said:**
> hi I am having the same problems here....
I just installed my ubuntu 7.10 (gutsy) and it seems that my video is a little slow... (and i can't enable desktop effects)

i think that my video-card is ok, i used to play warcraft III: TFT (Dota-Allstars) when i was using windows and the video was good. i never had problems playing games....

my graphics card is a **Intel 945G** integrated graphics controller

I attached my configs:


 lspci | grep VGA
compiz

gedit /etc/x11/xorg.conf

 sudo lshw -C Video


someone could help me please? 
thanks

Check this post:  [http://ubuntuforums.org/showthread.php?t=467775](http://ubuntuforums.org/showthread.php?t=467775)
It seems that somebody with your same video card had this working after a dpkg-reconfigure xserver-xorg

---

### Post by zuknivek on 2008-01-29
> **xeth_delta said:**
> You're welcome!  Have you tried to reconfigure?

```
sudo dpkg-reconfigure xserver-xorg
```

I reconfigured and i still can't enable my desktop effects. I think that there is a good possibility that my video card is just to crappy to handle it.

---

### Post by xeth_delta on 2008-01-29
> **zuknivek said:**
> I reconfigured and i still can't enable my desktop effects. I think that there is a good possibility that my video card is just to slow to handle it.

We wouldn't know until you have ahrdware acceleration working. That would be the first step. Don't lose hope, we'll keep trying till it works. I'll post when I get a new idea and hopefully someone else will also come with suggestions.

---

### Post by zuknivek on 2008-01-29
> **xeth_delta said:**
> We wouldn't know until you have ahrdware acceleration working. That would be the first step. Don't lose hope, we'll keep trying till it works. I'll post when I get a new idea and hopefully someone else will also come with suggestions.
ok then. thank you again for all of your help.

---

### Post by durand on 2008-01-29
I have an integrated Intel 945 built into my dell dimension, and it definitely worked with hardware acceleration and compiz. I'm now using an nvidia card so I can't really help you but just saying that it should work quite well.

---

### Post by dark_harmonics on 2008-01-30
Sorry I'm stumped here. From what I'm reading, reconfiguring the xorg and adding in the xorg.conf options from previous posts should fix this. I even read of somebody getting direct rendering on your similar model computer.

I hope you dont give up and keep plugging away. Even if compiz isn't running, your computer should be able to perform direct rendering.

---

### Post by zuknivek on 2008-01-30
> **dark_harmonics said:**
> Sorry I'm stumped here. From what I'm reading, reconfiguring the xorg and adding in the xorg.conf options from previous posts should fix this. I even read of somebody getting direct rendering on your similar model computer.

I hope you dont give up and keep plugging away. Even if compiz isn't running, your computer should be able to perform direct rendering.
Maybe i'm doing something wrong. There is this thing that i've done with msn messenger before on my computer that allows someone else to control my computer over the net. I have nothing to hide if you knew of a website that would allow you to control my computer over the net.

---

### Post by Beholder87 on 2008-01-30
Same problem here!: "No Direct Rendering"
i tryed to reconfigure the xorg.conf; ```
sudo dpkg-reconfigure xserver-xorg
```
to use those commands inside xorg:
> **xeth_delta said:**
> "...Now, in the <<Section "Module">>, change from...to...Section "Module" from...to.... etc....
tryed to go to this link and ask for help: [http://ubuntuforums.org/showthread.php?p=4236951#post4236951](http://ubuntuforums.org/showthread.php?p=4236951#post4236951)
but nothing seems to work.... i always get the message from glxinfo | grep direct:
[b]direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect[/b]

I don't know what else should I do.... my video here in ubuntu is pretty much slow... I can't even watch videos in youtube because it's too slow, and even when i scroll down web-pages, the video changes slowly..........

**Please I need Help!**

It seems that me and zuknivek are in the same situation.....
=/

---

### Post by xeth_delta on 2008-01-31
Hmm, seems to be some problem with the driver configuration, since none of you two have direct rendering enabled. I will try to reply soon with some fresh ideas, but I will have to ask for some patience :) The following two days I will be rather busy.

In any case, don't give up! We will get that working one way or another.
Xeth

---

### Post by Beholder87 on 2008-01-31
thanks xeth_delta 
=)

i tryed to google this problem but i couldn't find an answer too...
but i found that there is a log file about xorg:

**/var/log/Xorg.0.log** and it says in the 616 line:

```
(II) intel(0): **direct rendering: Enabled**
```

i guess that the **driver** is correct: **intel** for **945G** video Card. i tryed to use i810 (the old one), but it didn't helped me...

I Wont Give-Up on Linux!!! (this is the first time that i use linux (gutsy))
=)

---

### Post by xeth_delta on 2008-01-31
> **Beholder87 said:**
> thanks xeth_delta 
=)

i tryed to google this problem but i couldn't find an answer too...
but i found that there is a log file about xorg:

**/var/log/Xorg.0.log** and it says in the 616 line:

```
(II) intel(0): **direct rendering: Enabled**
```

i guess that the **driver** is correct: **intel** for **945G** video Card. i tryed to use i810 (the old one), but it didn't helped me...

I Wont Give-Up on Linux!!! (this is the first time that i use linux (gutsy))
=)

Glad to hear that determination. I use the i810 driver, if that helps.

Xeth

---

### Post by wesley_of_course on 2008-01-31
Hi All !  I myself use Nvidia but had trouble enabling "effects " , got it working with some perseverance  and this forum ,  anyway it seems a bug has been filed on it .
Bug #154104 in xserver-xorg-video-intel (Ubuntu)

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/154104](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/154104)

    About halfway down is an interesting reply ;

                [[IMG]https://bugs.launchpad.net/@@/person[/IMG] Sumant Oemrawsingh]("https://bugs.launchpad.net/%7Esoemraws")          wrote     on 2007-11-01:          [              (permalink)     ]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/154104/comments/15")   
               [FONT=monospace]Did you try to remove xserver-xorg-xgl? Whereas Feisty needed that, Gutsy doesn't anymore, and xserver-xorg-video-intel is all that is needed (for intel video cards of course).



   I am by NO  means advocating this because I don't have that challenge nor card . However reading the post thru might shed some light on this . Good Luck and don't give up .

[/FONT]

---

### Post by Beholder87 on 2008-01-31
> **wesley_of_course said:**
> 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/154104](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/154104)
[URL="https://bugs.launchpad.net/%7Esoemraws"][IMG]https://bugs.launchpad.net/@@/person[/IMG] 

Sumant Oemrawsingh[/URL]          wrote     on 2007-11-01:          [              (permalink)     ]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/154104/comments/15")   
               [FONT=monospace]Did you try to remove xserver-xorg-xgl? Whereas Feisty needed that, Gutsy doesn't anymore, and xserver-xorg-video-intel is all that is needed (for intel video cards of course).
[/FONT]

THANKS!!! THAT COMPLETLY SOLVED MY PROBLEM!!! Now my video is working 100%!!!!! No delay!!! It's PERFECT!!!
```
monster@monster:~$ glxinfo | grep direct
direct rendering: Yes
```

**the bug was a problem with** the GL: **xserver-xgl**
so i went to my terminal and used:

**1)** sudo synaptic to open the synaptic package manager
**2)** searched for the word: xserver-xgl
**3)** marked it to remove and aply!
**4)** CTRL+ALT+BAckSPace to reset X server
**5)** DONE!!!

**OR** just open terminal and use:

**1)** sudo apt-get remove xserver-xgl
**2)** CTRL+ALT+BACKSPACE
**3)** Done!

I hope that it can help you too zuknivek!

**THANK YOU ALL!!!!**

---

### Post by bloodhacker2 on 2008-01-31
Hey this is what i got.

Code:

bloodhacker@bloodhacker-desktop:~$ lspci | grep VGA
00:05.0 VGA compatible controller: nVidia Corporation C51 [Quadro NVS 210S/GeForce 6150LE] (rev a2)
bloodhacker@bloodhacker-desktop:~$ 
bloodhacker@bloodhacker-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0245 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

what drivers do i need for this.

---

