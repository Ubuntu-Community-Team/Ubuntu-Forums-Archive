---
title: "Compiz Fusion will not enable"
date: 2010-02-13
forum: Desktop Environments
---

### Post by billybag on 2010-02-13
I ahve always had ubuntu and compiz on my laptop (dell xps 1530)

I reinstalled ubuntu with the newest version (karmic)

I could not, for the life of me, get compiz to auto start. in an effert to fix this i purged and removed compiz. But now, after installing (and reinstalling) i cannot get compiz to work at all. it installs. it doesn't make any menu icons. When enabling visual effects through appearances menu, it says that it cannot be enabled.

```
$ compiz -fusion
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
metacity: Unknown option -fusion

```

```
$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
```

my xorg.conf
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

---

### Post by ajventi on 2010-02-19
I'm pretty sure you need the following lines in your xorg.conf for compiz to work: 

```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Just to make sure look for backups of your pre-update xorg.conf files, when you updated, dpkg should have backed them up on my system it looks like this:

```
anthony@alpha:~$ ls -la  /etc/X11/xorg.conf*
-rw-r--r-- 1 root root 1828 2010-02-16 21:44 /etc/X11/xorg.conf
-rw-r--r-- 1 root root 1837 2010-02-16 21:37 /etc/X11/xorg.conf~
-rw-r--r-- 1 root root 1362 2009-10-31 10:30 /etc/X11/xorg.conf.20091031103036
-rw-r--r-- 1 root root 1671 2010-02-16 13:31 /etc/X11/xorg.conf.backup
-rw-r--r-- 1 root root 1625 2010-02-16 12:32 /etc/X11/xorg.conf.backup~
-rw-r--r-- 1 root root 1225 2010-01-27 11:53 /etc/X11/xorg.conf.dist-upgrade-201001271153
-rw-r--r-- 1 root root  894 2010-02-16 21:42 /etc/X11/xorg.conf.failsafe
```

The files that end with ~ are from backups that I've hand edited, **xorg.conf.dist-upgrade-201001271153** is the backup made before I did my last dist-upgrade. I'm betting if you look in there it will have the Composite extension I listed above.

---

### Post by Hero of Time on 2010-02-20
Here's my xorg.conf with the nVidia proprietary driver:
```
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"        0 0
        InputDevice     "Logitech MX510"
EndSection

Section "ServerFlags"
        Option  "BlankTime"     "15"
        Option  "StandbyTime"   "15"
        Option  "SuspendTime"   "15"
        Option  "OffTime"       "15"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "altgr-intl"
        Option          "XkbOptions"    "lv3:ralt_switch:altwin:meta_win"
EndSection

Section "InputDevice"
        Identifier  "Logitech MX510"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Buttons"       "8"
        Option          "ZAxisMapping"  "4 5"
        Option          "ButtonMapping" "1 2 3 8 9 4 5 10"
EndSection

Section "Monitor"
        Identifier      "BenQ"
        Option          "DPMS"  "True"
EndSection

Section "Device"
        Identifier      "nVidia GeForce 7800 GTX"
        Driver          "nvidia"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia GeForce 7800 GTX"
        Monitor         "BenQ"
        DefaultDepth    24
        SubSection      "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection
```
No option for composite needed. What you need, is to fix the parts that compiz checks for. It already fails on the first test, Google for it or search this forum for a fix.
```
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
```
That's the bad stuff. Fix that and you probably have fixed the rest.

---

