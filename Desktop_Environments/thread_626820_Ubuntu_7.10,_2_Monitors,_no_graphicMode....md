---
title: "Ubuntu 7.10, 2 Monitors, no graphicMode..."
date: 2007-11-29
forum: Desktop Environments
---

### Post by xx6xx on 2007-11-29
Hi, 
first of all, I'm nooob in Ubuntu World, so sorry for my incompetence...

This is my problem:
I installed ubuntu 7.10 on my notebook (ASUS A8JP, ATI x1700) 2 days ago. My notebook is connected with a 22" TFT monitor Samsung 223BW.

I played with screen managment, so that I disable the TFT in my notebook while 22" TFT using, I enabled/disabled sth, perhapse primary/sedcondary monitor, changed resolution and did restart the system...
Now I can't get to graphic mode, while starting ubuntu only console starts... how do I get my graphic desktop again ???????

I can tip commands as root, i tried "sudo gdm" and "sudo /etc/init.d/gdm start,
 but the result was that both of my screens got black for a second, then concole appeard again, then again black screen 1 sec, console, black screen 1 sec and finally I land in console again, nothing more happens...

How can I repair that ?:confused:
How can I with commands restore my default screen options, so that it like after instalation ??
 THX for HELP.


OK,  I assume the problem is somewhere here:
Part of my xorg.conf:
```

...
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

...

Section "screen" #  
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1680x1050@60"	"1920x1200@60"	"1600x1024@60"	"1440x900@60"	"1440x900@75"	"1280x800@60"	"1280x768@75"	"1280x800@75"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" #  
	Identifier	"monitor1"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 226BW (Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection
...


```

ok, how can I fix it, what schould i delete ?

THX for Help...

---

### Post by jbt on 2007-11-29
> **xx6xx said:**
> 

I played with screen managment, so that I disable the TFT in my notebook while 22" TFT using, I enabled/disabled sth, perhapse primary/sedcondary monitor, changed resolution and did restart the system...
Now I can't get to graphic mode, while starting ubuntu only console starts... how do I get my graphic desktop again ???????

.....

I can tip commands as root, i tried "sudo gdm" and "sudo /etc/init.d/gdm start,
 but the result was that both of my screens got black for a second, then concole appeard again, then again black screen 1 sec, console, black screen 1 sec and finally I land in console again, nothing more 
THX for Help...

It sound like you have made a mistake while playing with screen management.
gdm is no longer able to start X. You are right that this is most likely a problem with xorg.conf

Usually the system tools make a backup of xorg.conf when they change it, so copying a working 

try the following:

sudo sh
cd /etc/X11
ls -lt | head

This will show you the most recent few files

Backup your current xorg.conf, and
try copying one of the more recent xorg.conf backup files to xorg.conf:

cp xorg.conf xorg.conf.not_working
cp xorg.conf.6 xorg.conf

then:
/etc/init.d/gdm restart


Regards
JohnT

---

### Post by twist2b on 2007-11-29
please post your graphics card.... if its a NVIDIA i can help you solve it.... its quite simple, but you just have to no the codes :P

---

### Post by xx6xx on 2007-11-29
I'm extremly greatful JohnT for your help, I didn't know, that backups are made automatic, I used an older conf File and now I'm runnig my Ubuntu again :D :D :D It's a pitty I'll probably have to install my ATI X1700 Drivers again, but never the less ubuntu works again

Many THX, I love ubuntu and it's society :D

---

