---
title: "Strange things happen when I run applications."
date: 2005-08-11
forum: Desktop Environments
---

### Post by fresco on 2005-08-11
Every time when I try to run mplayer, xscreensaver, glxgears, glxinfo, etc. I get the following message: "Segmentation fault". 

I tried to run *strace* before apps' names and I have noticed that every time this line appears:

access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)

I was messing with nvidia drivers and X configuration, that's all... Don't know what caused this problem.

Anyway, does any of you has had this kind of problem. How to fix it?

Thank you for help!   =;

---

### Post by anarki on 2005-08-11
[QUOTE=fresco]Every time when I try to run mplayer, xscreensaver, glxgears, glxinfo, etc. I get the following message: "Segmentation fault". 

I tried to run *strace* before apps' names and I have noticed that every time this line appears:

access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)

I was messing with nvidia drivers and X configuration, that's all... Don't know what caused this problem.

Anyway, does any of you has had this kind of problem. How to fix it?

Thank you for help!   =;[/QUOTE]
 Segmentation fault error - looks more like the application that you run have bug, then the settings of X are bad. Try to reinstall applications eventually using different mirror.

---

### Post by kassetra on 2005-08-11
[QUOTE=fresco]
I was messing with nvidia drivers and X configuration, that's all... Don't know what caused this problem.[/QUOTE]

When you say you were messing with the nvidia drivers and x config ... what exactly do you mean?  Do you remember what you did?  Do you remember the settings you had?  Did you make backup copies before editing?  Did those applications work before you changed things?

---

### Post by fresco on 2005-08-12
Well, I tried to install nvidia driver after I had upgraded to 2.6.10-5-k7. I reinstalled nvigia-glx and nvidia-settings via synaptic and ran all the steps from Ubuntu guide but it didn't work. It said: "Failed to load kernel module." So I downloaded linux-headers-2.6.10-5-k7 and installed driver manually. After the first restart everything worked good, second time I had booted the system it gave me an error.

By the way, in xorg.conf i disabled Load "dri', erased Section DRI, enabled Load "glx".

Many times I had to boot using "nv", not "nvidia"... Right now I am using "nv". You can see X output using "nvidia" in the attached file. 

The only modes I specified in xorg.conf are 800x600 and 640x480.
Why does it probe so many modes? (These is for example, there are much more in Xorg.0.log).

(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)

Also I created a partition, copied all the files from my homedir and mounted it on /home. But everything works fine there, I haven't seen errors come up.

xorg.conf.i386 is a backup file which worked when I was using i386 kernel.

There aren't many changes I have made:

nik@ubuntu:~$ diff /etc/X11/xorg.conf /etc/X11/xorg.conf.i386
39a40
>       Load    "dri"
70c71
<       Driver          "nv"
---
>       Driver          "nvidia"
115a117,120
>
> Section "DRI"
>       Mode    0666
> EndSection

Thanks!

---

### Post by Lord Illidan on 2005-08-12
k7? But do you have an AMD processor?

---

### Post by fresco on 2005-08-12
Yes, I dooo!  :razz: 

Just tried to boot i386 kernel but no results. Nothing changed.

---

### Post by Lord Illidan on 2005-08-12
You don't have to disable load glx... You have to disable load glcore...

---

### Post by fresco on 2005-08-12
Sorry, it was a typo in question. Fixed It. 
Here is my xorg.conf:

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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

Section "Device"
	Identifier	"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SAMTRON"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"SAMTRON"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

---

### Post by fresco on 2005-08-13
Sorry for my insistence, but I gotta fix this issue.  :grin:

---

### Post by fresco on 2005-08-13
Sorry for my insistence, but I gotta fix this issue.  :grin:

---

