---
title: "Trouble with Enemy Territory"
date: 2005-10-15
forum: Gaming &amp; Leisure
---

### Post by Uber_n00b on 2005-10-15
I'm sorry to bother you with my problems (especially on my first post :oops: ) but I'm pretty new to linux still, and could use some assistance.

I've downloaded and installed ET, but when i run it, nothing happens.  I tried running it in terminal, and this is the output:
----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Segmentation fault


Could anybody tell me what could cause this?  Any assistance would be greatly appreciated.  Thanks!

---

### Post by seethru on 2005-10-15
what video card? have you installed the proper drivers? did you modify your xorg.conf after installing said drivers?

---

### Post by Uber_n00b on 2005-10-15
Hmm...I guess it would have helped to list that.  Yes, I have installed the drivers already, and modified my xorg.conf.  I'm using a geforce 6600gt.  I could play it (w/o sound) when I used gentoo, but for some reason, I con't get it to run now.

Thanks for the prompt reply, btw!

Edit: Here's my xorg.conf.  tell me if something looks wrong.


Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
#	SubSection "Display"
#		Depth		1
#		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		4
#		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		8
#		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		15
#		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth		16
#		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
#	EndSubSection
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
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by seethru on 2005-10-15
did you install the nvidia drivers through apt-get, or did you install the ones off nvidia's website?

and whats the output of this command

```

ls -l /usr/lib | grep GL

```

---

### Post by Uber_n00b on 2005-10-15
Here's my output:

cameron@ubuntu:~$ ls -l /usr/lib | grep GL
lrwxrwxrwx   1 root root       21 2005-10-12 18:31 libGLcore.so.1 -> libGLcore.so.1.0.7667
-rw-r--r--   1 root root  7379792 2005-10-11 13:17 libGLcore.so.1.0.7667
lrwxrwxrwx   1 root root       17 2005-10-12 18:31 libGL.so.1 -> libGL.so.1.0.7667
-rw-r--r--   1 root root   705424 2005-10-11 13:17 libGL.so.1.0.7667
lrwxrwxrwx   1 root root       20 2005-10-11 01:45 libGLU.so.1 -> libGLU.so.1.3.060302
-rw-r--r--   1 root root   513304 2005-09-23 05:26 libGLU.so.1.3.060302

I used the drivers from the website.  Later, though (and I don't know if it makes a difference) I downloaded easy ubuntu (mainly just for the codecs and firefox plugins that didn't work anyway).  Do you suppose I should redo it?  or use apt-get?

---

### Post by seethru on 2005-10-15
thats probably the problem, and I personally am not too sure how to uninstall the drivers from nvidia.

---

### Post by Uber_n00b on 2005-10-15
Do you think I would need to uninstall the drivers, or just re-install?  Which drivers would I want to use?

---

### Post by Hokputooy on 2005-10-15
Try Uncommenting out "Load  GLcore" and "Load dri" under the module section.

---

### Post by Gnobody on 2005-10-15
[QUOTE=Hokputooy]Try Uncommenting out "Load  GLcore" and "Load dri" under the module section.[/QUOTE]


Do not uncomment Load GLcore or Load dri, they are for opensource and ATi drivers ONLY!  I wouldn't recommend installing the drivers via NVidia's installer but rather: 

sudo apt-get install nvidia-glx

You may have to remove some of the .so files that the installer left behind.

---

### Post by Gnobody on 2005-10-15
Actually you won't have to remove any of the libs left behind because they are the same version number.

---

### Post by Uber_n00b on 2005-10-15
This is my output when I apt-get nvidia-glx

Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://download.skype.com](http://download.skype.com) stable/non-free Packages (/var/lib/apt/lists/download.skype.com_linux_repos_debian_dists_stable_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

when I run apt-get update, this is what I get:

Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://download.skype.com](http://download.skype.com) stable Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release [19.6kB]
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Err [http://download.skype.com](http://download.skype.com) stable/non-free Packages
  404 Not Found [IP: 212.72.49.140 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 39.6kB in 1s (26.1kB/s)
Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404 Not Found [IP: 212.72.49.140 80]
Reading package lists... Done
W: Couldn't stat source package list [http://download.skype.com](http://download.skype.com) stable/non-free Packages (/var/lib/apt/lists/download.skype.com_linux_repos_debian_dists_stable_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by zazeem on 2005-10-16
i had this same problem with et cause i was also a nub. first install nvidia drivers and nvidia settings and nvidia glx or wtvr from synaptic, after that open your etc/x11/config and delete resolutions higher than 1024x768, then once et is running it is unlikely your sound will be working so use this as root
su
killall esd; et; esd
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

then restart x and try it again :)

---

### Post by Uber_n00b on 2005-10-16
So, basically what you're saying is that If I want to play ET, I can't have a resolution higher than 1024x768?  That would really suck.  Is it a problem unique to ubuntu?  I never had any problem wtih ET (other than sound) when I used Gentoo.  I'm hoping there's some other way around this.

---

### Post by Uber_n00b on 2005-10-20
Since I can't get it working is there any way to uninstall it (for the time being)

---

