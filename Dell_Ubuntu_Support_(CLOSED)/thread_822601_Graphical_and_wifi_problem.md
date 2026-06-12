---
title: "Graphical and wifi problem"
date: 2008-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Fransw on 2008-06-08
Hey everyone,

Recently, I switched my laptop from windows XP to Ubuntu 8.04. At this moment, I've got two major problems with it.

1. Wireless internet doesn't work.
2. Graphical drivers are likely not running. I'm trying to use Celestia (OpenGL), but it doesn't work nearly as smooth as it's supposed to work.

I'm an uber-linux-n00b (the switch to hardy is my first linux-experience ever), so I have no real idea where the problems could be.

My laptop was bought through a university-offer, so likely it isn't standard in terms of adapters.

Hardware:
Dell Inspiron 640m
CPU: Centrino Duo 1.66Ghz
videocard: Intel Graphics Media Accelerator 950TM
1024MB DDR2 RAM memory.
Intel Pro/Wireless 3945

I'm using a standard Ubuntu 8.04 32bit Desktop release, with the normal updates installed.

If someone is able to help me solve these two problems, I'll be very grateful.

With Regards,
Frans

---

### Post by sam_delta on 2008-06-09
first of all, i recomend you to make all updates, connect a wired internet cable and go into system>administration>update 
manager , click on check, then install,,, updates might help your problems

for your wireless it should just work, ,, 
can you open a terminal (aplications>accesories>termina) and type the following command
```
 sudo iwlist scan
```if the output list the available wireless networks, that means that your good to go, just click on the wireless icon on the top-right of your screen (top-right of your pannel at the task-bar, probably a small monitor icon), and select which network to connect to.

if the command returns no wireless networks, then you might want to read the following post [http://ubuntuforums.org/showthread.php?t=781472](http://ubuntuforums.org/showthread.php?t=781472) to get it working

NOTE----------its unlikely that the wireless wont work out of the box. (it should work out of the box, that wireless card is supported)

any questions, ill be around
tell us if you have a problem or how it goes

sam

---

### Post by Fransw on 2008-06-09
Update manager shows no new critical updates, which means it should be up to date.

sudo iwlist scan returns the following output:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:07:0E:15:A9:30
                    ESSID:"WLAN"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/100  Signal level:-86 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001fd9d441193
          Cell 02 - Address: 00:07:0E:15:A6:E0
                    ESSID:"WLAN"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/100  Signal level:-79 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000001fd9d144196

```

Tried connecting afterwards, and somehow it works. God knows how it came to be, since I'm fairly sure it didn't work when I tried the same stuff earlier... Well, I'm as of yet too inexperienced with linux to have an urge to figure it out exactly.

Still, the graphical problem remains. Which is fairly ****ty, since I'm a huge fan of Celestia, and used it extensively back in my windows-days.

By the way, a new problem that has occured is Nautilus. During startup I get an error that nautilus doesn't work. Could the cause be that I put a 7mb big wallpaper on my laptop? (sombrero galaxy, highres straight off wikipedia ^_^)

With regards,
Fransw

---

### Post by sam_delta on 2008-06-09
i dont know much about graphics, its better if someone else is able to help here, but let me see if i can find something by doing some research

sam

---

### Post by Fransw on 2008-06-14
Okay, I'll await that then. I tried searching around the internet for drivers for my video card, but the only useful hits the search engines return is this very thread ^_^

With regards,
Frans

---

### Post by sam_delta on 2008-06-14
hey, after reading some threads, i find that you can now download linux/ubuntu drivers for your graphic card, they might also be available in synaptic, post the output of the commands below, see if you can find the appropriate drivers in intel's website and ill see if i can find which drivers you should download from synaptic

also, can you post the ouput of the following 2 commands please```
cat /etc/X11/xorg.conf
cat /etc/modprobe.d/blackist 
```

sam

---

### Post by Fransw on 2008-06-15
output of cat /etc/X11/xorg.conf:
```
fransw@merlin:~$ cat /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

output of cat /etc/modprobe.d/blacklist (with an l):
```
fransw@merlin:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

```

I'll go hug the intel website in search of a driver for my graphics card.

With regards,
Frans

---

### Post by sam_delta on 2008-06-15
alright, thx, ill see what i can find
tell me if you find drivers somewhere in intel webpage

sam

---

### Post by Fransw on 2008-07-05
First of all: sorry for bumping up an old thread. I was extremely busy the past few weeks, so I had no time to work on the graphical problem which I still have. Until now.

I've found [http://www.intellinuxgraphics.org/](http://www.intellinuxgraphics.org/) which appears to have a "I8xx" driver pack, which supports the Intell 945GM chipset. As far as I can see, that's the one I need to get.

Problem is, the manual that's given there is rather technical and aimed at developers. I'm struggling just to get my machine running as I want it, so that's a level too hard for me.

Is there anyone here who can help me installing these drivers by advising me in a way that I understand it? You'll have my (near)eternal gratitude in return (and a cookie ^_^)

With regards,
Fransw

---

### Post by sam_delta on 2008-07-05
i think i found somethhing, , go into system>administration>synaptic package manager, 
search and install the following 2 packages:

xserver-xorg-video-i810
xserver-xorg-video-intel

then restart  your pc.

if it does nothing or the packages were already installed, open a terminal, and post the output of the commnad, ```
cat /etc/X11/xorg.conf
```

sam

---

### Post by Fransw on 2008-07-06
Both already appeared to be installed but I'm still having problems running Celestia.

output:
```
fransw@merlin:~$ cat /etc/X11/xorg.conf
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

With regards,
Fransw

---

### Post by sam_delta on 2008-07-07
im still trying to figure out whats going on, as i told you before, im not too good when it comes to graphics

anyways, the following command might be usefull ```
glxinfo | grep direct
```

sam

---

