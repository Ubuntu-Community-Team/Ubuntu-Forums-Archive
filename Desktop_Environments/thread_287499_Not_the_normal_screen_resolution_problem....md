---
title: "Not the normal screen resolution problem..."
date: 2006-10-28
forum: Desktop Environments
---

### Post by techweenie on 2006-10-28
I am new to ubuntu, but not forums.  I have searched and read up on all the possible solutions to fix resolution and refresh rate problems, but nothing has worked for me so far.  I have installed the nvidia driver which works great with my GeForce 7800GT, but now I'm stuck at 800x600@60Hz. My monitor is a 19" ViewSonic A91f+ which I'd like to run at 1280x960@75Hz.  I ran the 'sudo dpkg-reconfigure xserver-xorg' command and selected everything the way I wanted it, but that did not help.  I also manually entered the HorizSync and VertRefresh lines to the xorg.conf file as well as a custom Modeline for 1024x768@85Hz.  None of that has helped.  ](*,) I absolutely love ubuntu from what I've seen so far, but if this issue can't be fixed then I'm afraid I have to find another distro.

Here is my xorg.conf for reference... pretty typical I think.

```
Section "Device"
	Identifier	"NVIDIA Corporation NVIDIA Defualt Card"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-86
	VertRefresh	50-180
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Defualt Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by techweenie on 2006-10-29
Well I downloaded 6.10 today and went to check that out, but booting in both normal and safe graphics modes does not work.  I can see the background and mouse cursor just fine, but the loading window is heavily corrupted and causes the computer to freeze (but I can still move the mouse).  In 6.06 the safe graphics mode worked fine.  Also, I was using AMD64 for 6.06, but with 6.10 I tried Intel x86 so I could use the flash plugin for firefox.  I then went to try Fedora Core 6, but that has the same graphical issues when trying the graphical installer.  I swear every time I think I'm ready to use linux again it's two baby steps forward and one giant leap back.

---

### Post by whatintheworldisthat on 2006-10-29
Instead of editing xorg.conf directly you can do dpkg-reconfigure xserver-xorg and go through an ncurses based wizard, it has an option to select resolution, you have to select it with spacebar and then press enter(some people had trouble with this).

You can run sudo dpkg-reconfigure xserver-xorg, only after you go command line mode(ctrl + alt + f1), and to get out alt + 7. After applying changes  go to your desktop (alt f7), log out, and restart the xserver(ctrl + alt + backspace).

Before running the command do cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak to backup your xorg.conf, if you want to revert just switch the bak file with the normal on the above command.

---

### Post by CatKiller on 2006-10-29
I'm amazed that that xorg.conf lets you display anything - you've not specified the BusID of the graphics device. So I can't really help. Sorry.

---

### Post by techweenie on 2006-10-29
> **whatintheworldisthat said:**
> Instead of editing xorg.conf directly you can do dpkg-reconfigure xserver-xorg and go through an ncurses based wizard, it has an option to select resolution, you have to select it with spacebar and then press enter(some people had trouble with this).

You can run sudo dpkg-reconfigure xserver-xorg, only after you go command line mode(ctrl + alt + f1), and to get out alt + 7. After applying changes  go to your desktop (alt f7), log out, and restart the xserver(ctrl + alt + backspace).

Before running the command do cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak to backup your xorg.conf, if you want to revert just switch the bak file with the normal on the above command.

I have done all of that with no help.  This is why I made this thread.

---

### Post by techweenie on 2006-10-29
> **CatKiller said:**
> I'm amazed that that xorg.conf lets you display anything - you've not specified the BusID of the graphics device. So I can't really help. Sorry.

I re-ran dpkg-reconfigure xserver-xorg and put in PCI:1:0:0 for the BusID, which is correct according to lspci.  However, that did not solve my problem.

```
Section "Device"
    Identifier    "NVIDIA Corporation NVIDIA Defualt Card"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    30-86
    VertRefresh    50-180
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NVIDIA Defualt Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus" "SendCoreEvents"
    InputDevice     "cursor" "SendCoreEvents"
    InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

```

---

### Post by techweenie on 2006-10-29
I solved my problem.  Using 'Option          "UseEDID" "FALSE"' allowed me to change the screen resolution, but not the refresh rate.  I'll worry about the refresh rate later, as it's at 85Hz, which is fine.

---

### Post by CatKiller on 2006-10-29
Glad you got that bit sorted, anyway.

---

