---
title: "First time install on Inspiron 1501"
date: 2008-02-13
forum: Dell  Ubuntu Support
---

### Post by geebob on 2008-02-13
Greetings,
several nights ago, a voice came to me in the darkness.  It whispered “Install linux on your computer” and now I must obey.

I'm very new to this but I'm posting this in this forum instead of the absolute beginner forum because I want to benefit from other Dell users, especially since there have been some issues specific to dell laptops, particularly the buggy suspend  issue which is important to me.  Has this been fixed in Gibbon yet?  Until then, Fawn is my primary consideration.

I have a Dell 1501 laptop with 1.5 GB ram and an 80 gig harddrive.  The graphics card is an ATI Radeon express 1150 and wireless is a Dell wireles 1390 WLAN minicard

The most important thing for me right now is installation on my harddrive though I'll bring up all of the other issues.  First of all, I don't want to touch windows on this computer so I have to install linux on this in such a way that I can boot from windows.  I'm hoping this can be done.  I figured I would install ubuntu on a new partition.  I started to shrink my OS disk but it will only give me 18 GB to play with even though I have a little over 40.  I wanted to give linux about 25 and leave about 15 for my windows volume but windows had other ideas.  Is 18 enough?  I would think so given that ubuntu takes up less than 5 GB.  Surely the programs can't be too demanding.  Am I correct to assume that if I provide an empty volume for ubuntu, it can take that volume and leave windows alone?  Is this all to small and should I wait till I get a new harddrive in the future?

Second issue of importance is wireless.  I assume that I can just download Ndiswrapper and the driver through windows and then boot up and apply these to ubuntu.  Wireless is currently the only access I have to the internet so I don't see how I can get these pieces of software any other way.

Third issue is sleep mode/suspend.  When I booted off of the live DVD, I didn't have it.  How do I get it?  Once I get it, can I tie it to the lid of the laptop so it will go to sleep when I shut it (though that convenience is not that important.)

These issues all make a difference as to whether I will use ubuntu (and even linux) at all.  I will not risk getting rid of windows and I won't uninstall just to reinstall it as It is exactly the way I want it now.  Wireless access is a must.  Sleep capability is a must as battery life is an issue here.

Lesser issues:
I could not control the brightness of the monitor through software nor the hot keys.  The hot keys only gave me two brightness settings and they did not consistently work.

Frivolity:
Desktop effects did not work.  Of course I read the note that said it wouldn't work on all systems.  It froze my system.  Has this been fixed?  Is this an option on KDE and if so, could it be more reliable on KDE?  Without the desktop space cube (not sure if that's what it's called), my ability to impress women with my computer will be compromised.  Might this work with different newbie friendly distributions or am I completely out of luck because of my hardware?

The screen savers running off the live DVD were very resource hungry.  Please tell me this is just because they were running off the live DVD.  They ran the frequency of my AMD at 2 Ghtz (it usually runs at 800) and at 100 percent.  

At the end of the 1st video at [http://www.whylinuxisbetter.net/items/spatial_desktop/index.php?lang](http://www.whylinuxisbetter.net/items/spatial_desktop/index.php?lang) , there are these sweet looking fish swimming all over the desktop.  Is that available for ubuntu?

---

### Post by noname123 on 2008-02-14
I am running a dell 1501 ubuntu 7.10 does most of the work a good idea when you install is to hard wire your internet and it will automatically download bcm3xxcutter I think that is what it was called and at first boot it will tell you that forced drivers are available enable them .You will also want the compiz to do the desktop effects and my suspend works just fine. If you want i can walk you through some of what i did to get mine up and running here is my email [EMAIL="bgckrh@hotmail.com"]bgckrh@hotmail.com[/EMAIL]

---

### Post by vahnx on 2008-02-14
I also have a Dell Inspiron 1501 AMD Sempron 3500+ 1.8ghz processor, 80GB HDD, with ATI Radeon X1150 256MB Hyper Memory. I cannot get suspend working no matter what. I tried so many different things, from editing /etc/X11/xorg.conf to switching from the restricted drivers to using envy. Nothing works! 

To the first poster, if you wish to add Ubuntu in a dual boot, boot from the live disk, select install on disk and use the built in partiton editor. I selected 20GB for Ubuntu and I used over half of it, but if you wish to run Virtual Machines you might wanna consider 40GB, in the ext3 format. Also, don't forget the Linux swap file, which should be about the same or double your RAM.

A really, really good site is [www.ubuntu1501.com](www.ubuntu1501.com), it's a blog dedicated to getting Ubuntu 7.10 fully functional on the 1501. Unfortunately, he did not get suspend working yet from what I read. 

So above poster, please post here the exact stuff you did to get suspend working. I will give you one of my many old Runescape accounts if you please post details here, instead of getting everyone to email you.

---

### Post by noname123 on 2008-02-15
sorry about the email thing i am new to forums.I regret to tell you my suspend quit working but as soon as i get the fix i will post it.

---

### Post by geebob on 2008-02-15
Greetings noname,
could you share more about compiz?  I have compiz 3.6 and yet, last time I attempted to do window effects, my screen went blank white and I had to start over.  I checked the website and it didn't seem that compize 4 was an option for my graphics card but the expirimental 5 was and I'm not sure I want to venture those untested waters... unless you already have with your Inspiron 1501 and have found it functional.

Also, due to the suspend issues, I am not running ubuntu 7.10 but rather 7.04 which suspends perfectly.  So yes, I finally installed and after the install, suspend works fine.

---

### Post by vahnx on 2008-02-15
Compiz works on the ATI X1150 256MB HyperMemory graphics card. To get it working, I used Envy to install the latest ATI drivers.

```
me@mylaptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7059 Release

```

Here is my xorg.conf:
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
	Option		"VideoOverlay"		"on"
	Option 		"Textured2D" 		"on"
	Option 		"TexturedXrender" 	"on"
	Option		"MaxGARTSize"		"256"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x800"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "Extensions"
	Option 		"Composite" 	"Enable"
EndSection

Section "DRI"
	Mode 0666
EndSection
```

It should work fine.

---

### Post by noname123 on 2008-02-15
```
Install Xgl
In a terminal type:
sudo apt-get install xserver-xgl

Setting Up XGL
In a terminal type:
sudo gedit /usr/local/bin/startxgl.sh

and this to the file:
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
save and close file

Then make the xgl script executable by entering this into a terminal:
sudo chmod a+x /usr/local/bin/startxgl.sh

Creating a XGL Login
Make the script, by typing this into a terminal:
sudo gedit /usr/share/xsessions/xgl.desktop

add this text to the file:
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
save and close file

Remove Compiz & Desktop Effects
sudo apt-get remove compiz-core desktop-effects

If you have Beryl Installed Remove Beryl Too
In a terminal type:
sudo apt-get remove beryl-ubuntu beryl-manager emerald

If you want to use emerald as your decorator for Compiz Fusion do not remove the emerald package.

Add the Compiz Fusion Repository
In a terminal type:
sudo gedit /etc/apt/sources.list

Add this to the end of your your source list:
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
save and close file

Add the tuxfamily Repository Key
In a terminal type:
sudo wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -

Update Your System
In a terminal type:
sudo apt-get update

Install Compiz Fusion
In a terminal type:
sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf

Now you just have to log off, log into your Xgl session and run Compiz Fusion.

To run Compiz Fusion:
compiz --replace

To run the Compiz Setting Manager:
ccsm


```


i got this from redDEADresolve

---

### Post by noname123 on 2008-02-15
ok how do you do the little window thing????????:lolflag:

---

### Post by vahnx on 2008-02-15
If you're talking to me, type {code}Stuff in here{/code}, only use the square brackets instead of squiggily.

---

### Post by noname123 on 2008-02-15
thanks



```
Install Xgl
In a terminal type:
sudo apt-get install xserver-xgl

Setting Up XGL
In a terminal type:
sudo gedit /usr/local/bin/startxgl.sh

and this to the file:
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
save and close file

Then make the xgl script executable by entering this into a terminal:
sudo chmod a+x /usr/local/bin/startxgl.sh

Creating a XGL Login
Make the script, by typing this into a terminal:
sudo gedit /usr/share/xsessions/xgl.desktop

add this text to the file:
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
save and close file

Remove Compiz & Desktop Effects
sudo apt-get remove compiz-core desktop-effects

If you have Beryl Installed Remove Beryl Too
In a terminal type:
sudo apt-get remove beryl-ubuntu beryl-manager emerald

If you want to use emerald as your decorator for Compiz Fusion do not remove the emerald package.

Add the Compiz Fusion Repository
In a terminal type:
sudo gedit /etc/apt/sources.list

Add this to the end of your your source list:
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
save and close file

Add the tuxfamily Repository Key
In a terminal type:
sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -

Update Your System
In a terminal type:
sudo apt-get update

Install Compiz Fusion
In a terminal type:
sudo apt-get install compiz compizconfig-settings-manager compiz-plugins compiz-gnome compiz-fusion-plugins-extra compiz-fusion-plugins-unofficial libcompizconfig-backend-gconf

Now you just have to log off, log into your Xgl session and run Compiz Fusion.

To run Compiz Fusion:
compiz --replace

To run the Compiz Setting Manager:
ccsm

```

it was just meant for who ever told me how

---

### Post by noname123 on 2008-02-16
did that work for you Geebob? Gdesklets domt seeem to work so you need to get screenlets use this 


```
echo "deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe #Gilir's screenlets packages and some stuff you shouldn't use" | sudo tee -a /etc/apt/sources.list

sudo apt-get update
sudo apt-get install screenlets
```

---

### Post by geebob on 2008-02-16
I tried installing the ati drivers but when I looked at the configuration, i had no luck.  Also, I upgraded to compiz 0.5.2 after all but it doesn't do anything, nothing that I can tell.  I've checked desktop cube, wobbly windows and several other effects but I get nothing.  At least it doesn't crash my computer.

to get the ati drivers, I did a little looking and found envy 0.9.10, installed it and ran it to install ATI drivers, rebooted when istructed, but when i tried that command posted by vahnx all I got was this

```
rob@friend:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
```
 and compiz manager still does nothing.

little help for a bull in a china shop fellas?

---

### Post by geebob on 2008-02-16
we posted about the same time noname so I didn't try what you had there yet until now.  I should probably still get that ATI driver but I'm at a loss as to how to do it.

---

### Post by geebob on 2008-02-16
okay, here's the current damage I've been doing
where vahnx has the openGL string of 2.1... and so on for his ATI driver, I have managed to get 2.0 by means of manually installing ("manual" via envy).

I attempted to work the code from nonames thread and I don't know what good that did.  here's the log:

```
rob@friend:~$ sudo apt-get install xserver-xgl
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libglitz-glx1 libglitz1
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 1843kB of archives.
After unpacking 4825kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com feisty/main libglitz1 0.5.6-1 [76.6kB]
Get:2 http://us.archive.ubuntu.com feisty/main libglitz-glx1 0.5.6-1 [29.6kB]
Get:3 http://us.archive.ubuntu.com feisty/universe xserver-xgl 7.2.0.git.20070224-0ubuntu3 [1737kB]
Fetched 1843kB in 11s (157kB/s)                                                
Selecting previously deselected package libglitz1.
(Reading database ... 120603 files and directories currently installed.)
Unpacking libglitz1 (from .../libglitz1_0.5.6-1_i386.deb) ...
Selecting previously deselected package libglitz-glx1.
Unpacking libglitz-glx1 (from .../libglitz-glx1_0.5.6-1_i386.deb) ...
Selecting previously deselected package xserver-xgl.
Unpacking xserver-xgl (from .../xserver-xgl_7.2.0.git.20070224-0ubuntu3_i386.deb) ...
Setting up libglitz1 (0.5.6-1) ...

Setting up libglitz-glx1 (0.5.6-1) ...

Setting up xserver-xgl (7.2.0.git.20070224-0ubuntu3) ...
rob@friend:~$ sudo gedit/usr/local/bin/startxgl.sh
sudo: gedit/usr/local/bin/startxgl.sh: command not found
rob@friend:~$ sudo gedit /usr/local/bin/startxgl.sh
rob@friend:~$ sudo chmod a+x /usr/local/bin/startxgl.sh
rob@friend:~$ sudo gedit /usr/local/bin/startxgl.sh
rob@friend:~$ sudo apt-get remove compiz-core desktop-effects
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package desktop-effects is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libsm-dev libice-dev x11proto-xext-dev x11proto-kb-dev x11proto-xinerama-dev
  x11proto-render-dev libxrender-dev libcompizconfig-backend-gconf
  mesa-common-dev libxdmcp-dev libstartup-notification0-dev libpng12-dev
  x11proto-composite-dev xtrans-dev x11proto-core-dev libxcursor-dev
  x11proto-randr-dev x11proto-damage-dev libxext-dev libxdamage-dev
  x11proto-input-dev x11proto-fixes-dev libxau-dev libxcomposite-dev
  libgl1-mesa-dev libxrandr-dev libx11-dev libxfixes-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  compiz compiz-core compiz-dev compiz-fusion-plugins-extra
  compiz-fusion-plugins-main compiz-gnome compiz-plugins
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 11.6MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 120636 files and directories currently installed.)
Removing compiz ...
Removing compiz-gnome ...
Removing compiz-plugins ...
Removing compiz-dev ...
Removing compiz-fusion-plugins-extra ...
Removing compiz-fusion-plugins-main ...
Removing compiz-core ...
rob@friend:~$ sudo gedit /etc/apt/sources.list
rob@friend:~$ sudo wget 
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
rob@friend:~$ sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
[http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg): Unsupported scheme.
gpg: no valid OpenPGP data found.
rob@friend:~$ sudo apt-get update
E: Malformed line 47 in source list /etc/apt/sources.list (URI parse)
rob@friend:~$ sudo apt-get update
E: Malformed line 47 in source list /etc/apt/sources.list (URI parse)
rob@friend:~$ sudo apt-get update

```

I gave up since this ends with a malformed line

I'm not confident that I did the scripting right either.  the forum turns some of the script to smileys so I used the quote function in hopes that that would give me the actual code;

in the gedit screen I have the following script

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

I don't know what it matters but alot of that pasted in a variety of colors and I don't know that the spacing remained the same between copy and pastes.

I think I'm finished experimenting on my own as far as this business of graphics is concerned

---

### Post by geebob on 2008-02-16
noname, I got locked out of both synatpic and add/remove and the computer claimed it had something to do with the repository lists (I think) I went back into the script and had to delete the item from post number 11 and I think I deleted another ittem and now both programs work again.

On the up side, I just found that I have screenlets, but I don't know when I got them but I assume it had to do with some of the code you posted here.

---

### Post by noname123 on 2008-02-16
OK the ati drivers i got were ready to install on first login i got message about forced drivers and i went threw the steps and it used the cutter automatically as for the repository list i will compare the post with my notes mabey i missed a letter on copy the cube and wobally window i was wondering if you right clicked on desktop\change desktop background\visual effects\custom?

---

### Post by noname123 on 2008-02-16
by the way i had suspend working it worked about to times then i had to completely reinstall ubuntu.Used every thing i posted worked fine?Well let me know how it gos.  :lolflag:




ps: the screenlets was post #11

---

### Post by noname123 on 2008-02-16
ok yall ati drivers


```
synaptic package manager install 
restricted-manager
restricted-manager-core
]Then you need bcm43xx-fwcutter
```

close synaptic

```
then go to System\admen.\restricted drivers manager 
```

please give me a heads up on how it goes 


also to get a full cube you must have four desktops enabled :)

---

### Post by geebob on 2008-02-16
Thanks for your trouble noname.  For the moment, for the most part, I'm going to give  most of wrestling with ubuntu a rest for a couple of days, but I'll try these things out later and let you know.

---

### Post by noname123 on 2008-02-16
no problem i had fun helping i hope it works 


ps i fixed a few of my posts

---

