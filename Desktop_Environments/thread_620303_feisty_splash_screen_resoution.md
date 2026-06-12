---
title: "feisty splash screen resoution"
date: 2007-11-22
forum: Desktop Environments
---

### Post by jlhughes on 2007-11-22
**EDIT**: Got my version mixed up. I'm running Gutsy.

I did a clean install of Gutsy on a system that had been running Feisty. The only problem I'm having is the splash screen. (Didn't have this issue with Edgy.) 

The panel with the login options appears off the screen on the bottom.  Once I log in I can correct this by setting the user screen resolution.

Apparently the system thinks the screen size should be 1280x1024 but it needs to be 1280x960.

How do I change the xorg.conf file so that the splash screen defaults to 1280x960?

Here's the existing xorg.conf section on the monitor.

Section "Device"
	Identifier	"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

---

### Post by Vince00 on 2007-11-22
Backup your xorg.conf before doing this just in case you need to restore your settings...

In Gutsy I just restored my section back to 1280x1024 after blitzing the startup screen and it was showing 800x600...

I'm suspecting you need to add a line to your screen section right below default depth as :

**Modes           "1280x960@60"**

Good Luck...
Vince

---

### Post by jlhughes on 2007-11-22
changing xorg.conf from:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

```

to:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	Modes		"1280x960@60"
EndSection

```

breaks the system.

Did I put the line in the wrong area?

---

### Post by erginemr on 2007-11-26
Hello,

Your xorg.conf file should look like this:

```

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV17 [GeForce4 MX 440]"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Modes   "1024x768_75"   "800x600_75"    "640x480_75"
        EndSubSection
EndSection

```

So, you should put the modes section inside a SubSection.

---

### Post by jlhughes on 2007-11-27
Tried using subsection like this:

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes "1280x960_60"
	EndSubSection
EndSection

```

This had no effect.

As the machine boots, the Ubuntu splash screen and the progress bar look excellent.  As the X loads, the screen announces that the monitor is doing an automatic resize. Everything is OK for a few sections, but by the time the prompt to enter the user name appears the screen has adjusted in such a way that the lower panel is almost completely off the screen. (You can still catch the edge of the panel and access the options.)

Clearly, this is NOT a fatal issue. I can live with this since the desired resolution is one of the options available and it is stored correctly between sessions.

---

### Post by erginemr on 2007-11-27
Could you please also try:

Modes "1280x960@60"

instead of 

Modes "1280x960_60"

just to be sure...

---

### Post by mrmiserable on 2007-11-27
do you mean login screen if so 

sudo gedit /etc/usplash.conf 

# Usplash configuration file
xres=1280
yres=960

change it to this and reboot to see if this works or try this

sudo dpkg-reconfigure -phigh usplash

---

### Post by jlhughes on 2007-11-28
Changed usplash.conf
# Usplash configuration file
xres=1280
yres=1024

to:
# Usplash configuration file
xres=1280
yres=960

and also tried sudo dpkg-reconfigure -phigh usplash

Rebooted computer. The screen still jumps back to 1280x1024 when the login prompt appears.

---

### Post by erginemr on 2007-11-28
> **jlhughes said:**
> Changed usplash.conf
# Usplash configuration file
xres=1280
yres=1024

to:
# Usplash configuration file
xres=1280
yres=960

and also tried sudo dpkg-reconfigure -phigh usplash

Rebooted computer. The screen still jumps back to 1280x1024 when the login prompt appears.

This seeting is related to the part before the login prompt, affecting the screen, where the Ubuntu logo and an orange progress bar appears.

Did you try: Modes "1280x960@60" instead of Modes "1280x960_60"
in the xorg.conf file?

---

### Post by erginemr on 2007-11-28
> **jlhughes said:**
> Changed usplash.conf
# Usplash configuration file
xres=1280
yres=1024

to:
# Usplash configuration file
xres=1280
yres=960

and also tried sudo dpkg-reconfigure -phigh usplash

Rebooted computer. The screen still jumps back to 1280x1024 when the login prompt appears.

This seeting is related to the part before the login prompt, affecting the screen where the Ubuntu logo and an orange progress bar appears.

The login and desktop are handled by /etc/X11/xorg.conf file.

Did you try: Modes "1280x960@60" instead of Modes "1280x960_60"
in the xorg.conf file?

EDIT: Sorry for double posting...

---

### Post by jlhughes on 2007-11-28
> **erginemr said:**
> 
Did you try: Modes "1280x960@60" instead of Modes "1280x960_60"
in the xorg.conf file?

I have the xorg.conf set
```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes "1280x960@60"
        EndSubSection
EndSection


```

And the usplash.conf
```

 Usplash configuration file
xres=1280
yres=960

```

I still get the original issue: At the login prompt, the screen defaults to 1280x1024, which pushes the bottom panel off the screen.

---

### Post by erginemr on 2007-11-28
> **jlhughes said:**
> 
I still get the original issue: At the login prompt, the screen defaults to 1280x1024, which pushes the bottom panel off the screen.

Sorry to hear that. Two questions:

1- From where do you get the information that the screen is 1280x1024, from an OSD issued by the LCD display?

2- Do you have any real buttons on your monitor, so that you can adjust the schreen height-depth ratio and edges from there?

---

### Post by jlhughes on 2007-11-28
> 1- From where do you get the information that the screen is 1280x1024, from an OSD issued by the LCD display?


When I originally installed Gutsy (sorry about that Feisty reference), both the login screen and the desktop after I logged in suffered the same defect -- the lower panel pushed off the bottom of the screen. When logged in, I checked preferences/screen resolution and it said the screen was set to 1280x1024. I changed this to 1280x960 to fix the desktop. However, the login screen still pushes the options panel off the screen (although I can still catch a piece of it with my mouse).


> 2- Do you have any real buttons on your monitor, so that you can adjust the schreen height-depth ratio and edges from there?


I have buttons, but they do not allow me to squeeze 1024 into a 960 hole. And even if the screen did allow that, the effect would be distort the desktop.

---

### Post by erginemr on 2007-11-28
The following community help site:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
discusses resolution issues in depth. You should check if you can make something out of it.

Normally, it should not be needed for a config file with a single depth (24 bit), but could you please add the line in red below and restart the X server with Ctrl+Alt+BackSpace just to make sure:

```

Section "Device"
Identifier "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
Driver "sis"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
Monitor "Generic Monitor"
DefaultDepth 24
        SubSection "Display"
        	[COLOR="Red"]Depth     24[/COLOR]
                Modes "1280x960@60"
        EndSubSection
EndSection

```

If it does not work either, I have one final shot. The community help site above refers to two command line programs: 
"sudo ddcprobe | grep monitorrange" and "gtf"

The first of these shows the horizontal and vertical sync rates for your monitor. For instance, when I issue "sudo ddcprobe | grep monitorrange", I get:

[COLOR="Blue"]monitorrange: 30-70, 50-160[/COLOR]

You should make sure that they match with:
```

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
[COLOR="Red"]HorizSync 30-70
VertRefresh 50-160[/COLOR]
EndSection

```

While the second command gives you the correct mode-line settings for a given resolution and refresh rate, which you can put into your xorg.conf file to "teach" the system how to use that resolution. When I issue: "gtf 1280 960 60", I get:

[COLOR="Blue"]# 1280x960 @ 60.00 Hz (GTF) hsync: 59.64 kHz; pclk: 102.10 MHz
Modeline "1280x960_60.00"  102.10  1280 1360 1496 1712  960 961 964 994  -HSync +Vsync[/COLOR]

You may try inserting this line into the following post:
```

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-160
[COLOR="Red"]Modeline "1280x960_60.00"  102.10  1280 1360 1496 1712  960 961 964 994  -HSync +Vsync[/COLOR]
EndSection

```

See any of these helps. Otherwise, sorry but I am out of my resources. :(

---

### Post by erginemr on 2007-11-28
You may also go over the following howto:
[http://ubuntuforums.org/showpost.php?p=454217](http://ubuntuforums.org/showpost.php?p=454217)

which underlines, among other things, the importance of the xorg log file:

/var/log/Xorg.0.log

in pinpointing the problems.

You can also check that file (which is quite long) from "system logs" application under Main Menu -> System -> Administration. Within that file, try to catch what happens when the X server tries to change the resolutions.

EDIT: On my previous post, when you write [COLOR="Blue"]Modeline "1280x960_60.00" ... [/COLOR], I believe you should write the same for the section [COLOR="Blue"]Modes "1280x960@60"[/COLOR]. So, if it does not work, you should try changing the first to: [COLOR="Blue"]Modeline "1280x960@60" ... [/COLOR]

---

### Post by jlhughes on 2007-11-29
I want to thank everyone for all the help with this issue. But I give up.

I tried each of erginemr's suggested modifications. Nothing helped.

As I mentioned earlier, this is only a problem before logging in and it is fixed once I log in. So I'll just live with it for now.

---

