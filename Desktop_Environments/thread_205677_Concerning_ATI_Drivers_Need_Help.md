---
title: "Concerning ATI Drivers: Need Help"
date: 2006-06-28
forum: Desktop Environments
---

### Post by Cyclohexane on 2006-06-28
Sigh..

Ok so recently, i've learned that I haven't been using my video card drivers, and have instead been using some lame Mesa thing.. This is what I believe (from what I've read) to be causing me to be virtually unable to play 3D games, such as CS 1.6, or Cube, or even Doom.. 

I have tried a guide on these forums (cannot find the thread =/... Something like "Installing ATI Drivers 0.2" or something)
I've also tried the ATI Ubuntu Wiki guide, and even the guide on the ATI Site.. 

Nothing works... I put in the command "fglrxinfo" and i get:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I really do not understand this.. Any help would be appreciated, thanks..

And btw.. If it matters, I have an ATI Radeon 9800 Pro video card

---

### Post by gerbman on 2006-06-28
[QUOTE=Cyclohexane]Sigh..

Ok so recently, i've learned that I haven't been using my video card drivers, and have instead been using some lame Mesa thing.. This is what I believe (from what I've read) to be causing me to be virtually unable to play 3D games, such as CS 1.6, or Cube, or even Doom.. 

I have tried a guide on these forums (cannot find the thread =/... Something like "Installing ATI Drivers 0.2" or something)
I've also tried the ATI Ubuntu Wiki guide, and even the guide on the ATI Site.. 

Nothing works... I put in the command "fglrxinfo" and i get:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I really do not understand this.. Any help would be appreciated, thanks..

And btw.. If it matters, I have an ATI Radeon 9800 Pro video card[/QUOTE]I'm assuming the Wiki guide you tried is [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") one. If not, give that one a try (worked for my 9500 Pro). If that doesn't work, post your /etc/X11/xorg.conf file.

---

### Post by Cyclohexane on 2006-06-28
[QUOTE=gerbman]I'm assuming the Wiki guide you tried is [this]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") one. If not, give that one a try (worked for my 9500 Pro). If that doesn't work, post your /etc/X11/xorg.conf file.[/QUOTE]

Actually it was [this one]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")..

I did look at that one, though.. It was pretty much the same thing I did.. Except that site told me to do this:

Under Section "Screen" The Identifier line needs to be changed to:

     Identifier "aticonfig-Screen[0]"

I did that, and still no luck.. :(

Here's my xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "BenQ FP91G+"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor    "BenQ FP91G+"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

Note: This is excluding the commented stuff up top..

---

### Post by gerbman on 2006-06-28
Hmmm...it looks almost exactly like mine. Did you restart the X server after making the changes recommended on the Wiki?

---

### Post by littlespy on 2006-06-28
you need the flgrx driver to play 3d games, after you change it from ati in your xorg file it should work with 3d acceleration

---

### Post by jgcamp99 on 2006-06-28
Do this step by step logged in as root and in an x-terminal window and you should get them on quickly and painlessly (you can even cut and paste each line of code into the x-terminal then run that line of command/code, be patient some lines of code take longer to complete than others and when done it returns you to another prompt for the next line of code), it's been modified from the sudo method in another thread on these forums. I prefer root to sudo, but that's just personal preference:

Installing the new driver

Download the ATI driver installer: 32bit Installer

This guide refers to the 32bit version of the driver. If you are using a x86_64 System you need the 64bit Installer. The installation procedure should be the same as for 32bit, except some filenames will differ slightly.

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.

Install necessary tools:

Code:

apt-get update 
apt-get install module-assistant build-essential
apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base


Create .deb packages:

Code:

chmod +x /ati-driver-installer-8.26.18-x86.run 
/ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper


Install .deb packages:

Code:

dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb 
dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb 
dpkg -i fglrx-control_8.26.18-1_i386.deb


Remove any old fglrx deb's from /usr/src/:

Code:

rm /usr/src/fglrx-kernel*.deb

(Note: the rm only needs to be done if you've had a prior version of ATi's drivers installed. You can also navigate to that folder and move the file to the trash bin.)

Compile the kernel module:

Code:

module-assistant prepare,update 
module-assistant build,install fglrx 
depmod


Note: You have to recompile the kernel module after each kernel update!

Update the xorg.conf file:

Code:

aticonfig --initial 
aticonfig --overlay-type=Xv


Reboot.

Confirm that it worked

Code:

$ fglrxinfo
display: :0.0 screen: 0 
OpenGL vendor string: ATI Technologies Inc. 
OpenGL renderer string: RADEON 9700 Generic 
OpenGL version string: 2.0.5879 ( 8.26.18 )

---

### Post by Cyclohexane on 2006-06-28
Thanks guys..

Gerbman: Yes, I restarted the X server.. 
Littlespy: Oh, thanks.. I just changed it.. I'm restarting after I post this.. 
jgcamp99: If you paid any attention to what I previously said, you would have noticed that you copy and pasted what was on the site I saw here.. Nice try..

---

### Post by jgcamp99 on 2006-06-28
"jgcamp99: If you paid any attention to what I previously said, you would have noticed that you copy and pasted what was on the site I saw here.. Nice try.."

I don't take offense, just tried to help you out because obviously, what you are getting and what I and others got by following instructions to the letter are two different things, why do others get them to work and you can't ? Obviously you didn't follow instructions. If you paid attention, this is what you would have coming up like everyone else (this directly from x-terminal on my system, I have no doubts yours will indicate a 9800 Pro of some nature when done properly). 

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5879 ( 8.26.18 )

Because not only did it work for 8.25.18 which I got on for my ATi Radeon 9600 XT over the weekend, I also got 8.26.18 upgraded using the same methodology in the past day or so and it took me just a few minutes. I saved this as a text file so I wouldn't have to hunt it down as ATi changes drivers out like socks or underwear.

So I'd say that you are more worthy of the: "Nice Try" award for this evening.

---

### Post by Cyclohexane on 2006-06-28
Mmk.. Well jg, I did follow it down to the letter, yet it still seems not to work..

Anyways, I rebooted after editing my xorg.conf by changing the ati driver setting to fglrx.. Well.. The x-server didn't boot, and it gave me an error reguarding my xorg.conf.. So I tried to copy my backup over the real thing, but I accidentally did the opposite.. So then I did sudo dpkg-reconfigure -phigh xserver-xorg.. so now here I am again, back at page 1..

Edit: Changed flgrx to fglrx

---

### Post by jgcamp99 on 2006-06-28
[http://www.ubuntuforums.org/showthread.php?t=189000&page=7&highlight=ati+drivers+installation](http://www.ubuntuforums.org/showthread.php?t=189000&page=7&highlight=ati+drivers+installation)

Here's the link, you can bookmark it with Firefox.

I see you're doing it as sudo, I have had issues with sudo before installing drivers and applications that weren't done thru the magic of Synaptic Package Manager or the Application Add/Remove, that's why the first thing I did was re-enable root to login. I also made sure that root and my Ubuntu user were both listed on the Groups in the System, Administration, User & Groups configuration. I am still free to use sudo, but at the same time, I can be root and do what I need to do as well.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Going back to a traditional root account

Enabling the root account

To enable the root account (i.e. set a password) use:

sudo passwd root

Enter your existing password
Enter password for root
Confirm password for root 

Then you must do this:

In Gnome

    *      Open System --> Administration --> Login Screen Setup
    *      Click on the security tab
    *      Check Allow root login

In KDE

    *      Open Konqueror and open the /etc/kde3/kdm/ folder
    *      Right click the kdmrc file and then Actions --> 'Edit as root'
    *      On line 246 should be AllowRootLogin=false change it to 'true'
    *      Save and exit.

---

### Post by Cyclohexane on 2006-06-28
Hmm.. Ok.. I think I have eyed an error (maybe not).. I'll try what I think I screwed up, then I'll see if logging in as root helps.. Thanks..

---

### Post by jgcamp99 on 2006-06-28
"chmod +x /ati-driver-installer-8.26.18-x86.run"

This aspect of it can be accomplished easily by going to the installer file itself and right clicking on it and opening the properties window, from there, make sure all boxes for permissions are checked for read, write and execute for Owner, Group and Others.

---

### Post by Cyclohexane on 2006-06-28
Alright.. Didn't work again, so I had to revert.. Gonna try the tutorial as root.. 

Gerbman: Would you mind posting your xorg.conf? I know it will have differences, but maybe i'll spot something that I was missing before.. 

And if anyone else has other input, please post.. Thanks

---

### Post by gerbman on 2006-06-28
[QUOTE=Cyclohexane]Alright.. Didn't work again, so I had to revert.. Gonna try the tutorial as root.. 

Gerbman: Would you mind posting your xorg.conf? I know it will have differences, but maybe i'll spot something that I was missing before.. 

And if anyone else has other input, please post.. Thanks[/QUOTE]Attached.

---

### Post by Cyclohexane on 2006-06-28
Hmm.. Well.. Still no luck.. =/..

I tried the tutorial under root.. and that didn't work.. 
Then I tried messing with gerbman's xorg.conf file to see if I was missing something... No luck.. :(

---

### Post by jgcamp99 on 2006-06-28
What might be in order is a step by step of the results of each command line of the manual install. This way others helping can see what is happening.

---

### Post by Cyclohexane on 2006-06-28
Alright.. I'll do that..

I'll edit this post to show the results..

I'll try the Method 1 in [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

Installing the driver

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!

I have all repositories enabled..

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
```
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.15-25-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
sudo apt-get install xorg-driver-fglrx
```
Reading package lists... Done
Building dependency tree... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
sudo depmod -a
sudo aticonfig --initial
```
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-1
```
sudo aticonfig --overlay-type=Xv
```
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-4
```

Reboot

Rebooting, now..

Ok.. Rebooted.. Now it says:

Confirm that it works
fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

---

### Post by Cyclohexane on 2006-06-29
Here's with method 2

Note: I uninstalled the drivers that it tells me to do if it doesn't work..

blacklist old fglrx module from linux-restricted-modules

sudo gedit /etc/default/linux-restricted-modules-common
Edited the file so: DISABLED_MODULES="fglrx"

Download the ATI driver installer: 32bit Installer
And I did that.. 

Change to the download directory. Make sure that you have the universe and multiverse repositories enabled in /etc/apt/sources.list before doing these steps.
Did that already.. 

sudo apt-get update
sudo apt-get install module-assistant build-essential
```
Reading package lists... Done
Building dependency tree... Done
module-assistant is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
```
fakeroot is already the newest version.
dh-make is already the newest version.
debconf is already the newest version.
libstdc++5 is already the newest version.
gcc-3.3-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
```
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.26.18..................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/dapper
/tmp/fglrx.qEFlwX ~/fglrx-install
Package /home/myron/xorg-driver-fglrx_8.26.18-1_i386.deb has been successfully generated
Package /home/myron/xorg-driver-fglrx-dev_8.26.18-1_i386.deb has been successfully generated
Package /home/myron/fglrx-kernel-source_8.26.18-1_i386.deb has been successfully generated
Package /home/myron/fglrx-control_8.26.18-1_i386.deb has been successfully generated
Package /home/myron/fglrx-sources_8.26.18-1_i386.deb has been successfully generated
~/fglrx-install
Removing temporary directory: fglrx-install

```
sudo dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb
```
Selecting previously deselected package xorg-driver-fglrx.
(Reading database ... 121949 files and directories currently installed.)
Unpacking xorg-driver-fglrx (from xorg-driver-fglrx_8.26.18-1_i386.deb) ...
Setting up xorg-driver-fglrx (8.26.18-1) ...
Starting atieventsd: done.

```
sudo dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb
```
Selecting previously deselected package fglrx-kernel-source.
(Reading database ... 122046 files and directories currently installed.)
Unpacking fglrx-kernel-source (from fglrx-kernel-source_8.26.18-1_i386.deb) ...
Setting up fglrx-kernel-source (8.26.18-1) ...

```
sudo dpkg -i fglrx-control_8.26.18-1_i386.deb
```
Selecting previously deselected package fglrx-control.
(Reading database ... 122050 files and directories currently installed.)
Unpacking fglrx-control (from fglrx-control_8.26.18-1_i386.deb) ...
Setting up fglrx-control (8.26.18-1) ...

```
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare,update
```
Getting source for kernel version: 2.6.15-25-386
Kernel headers available in /usr/src/linux

Done!

Updated infos about 70 packages

```
sudo module-assistant build,install fglrx
```
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Done with /usr/src/fglrx-kernel-2.6.15-25-386_8.26.18-1+2.6.15-25.43_i386.deb .
Selecting previously deselected package fglrx-kernel-2.6.15-25-386.
(Reading database ... 122057 files and directories currently installed.)
Unpacking fglrx-kernel-2.6.15-25-386 (from .../fglrx-kernel-2.6.15-25-386_8.26.18-1+2.6.15-25.43_i386.deb) ...
Setting up fglrx-kernel-2.6.15-25-386 (8.26.18-1+2.6.15-25.43) ...

```
sudo depmod -a
sudo aticonfig --initial
```
Found fglrx primary device section
Nothing to do, terminating.

```
sudo aticonfig --overlay-type=Xv
```
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-5

```
Reboot.

Rebooting right now... Maybe it'll work this time..

Or not... 

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

---

### Post by jgcamp99 on 2006-06-29
Since this has been hosed so many times, it doesn't hurt to run this command in terminal:

sh ./fglrx-uninstall.sh

My assumption is that it gets you back to Ubuntu's default installation driver. If it can't do it, just assume that ATi drivers have never been on your system.

Step 1: Log in as root, 
On the top Menubar: Places, Computer and locate the file "ati-driver-installer-8.26.18-x86.run"
Right click on the icon, Properties, Permissions and make sure that:

Owner, Group & Others has Read, Write and Execute boxes checked !

Copy that same file after changing permissions to the filesystem by opening another Places, Computer, you should see the Filesystem drive

Step 2: On the top Menubar, Applications, Accessories, Terminal, it opens your Gnome Terminal

type: cd /home/campjg/ (this is the directory where the "ati-driver-installer-8.26.18-x86.run" is located. It should return:

root@UBUNTU606LTS:/home/campjg#
(indicating the directory change)

I will assume that all the other files were properly downloaded and installed from these terminal command actions at this point in time:

apt-get update 
apt-get install module-assistant build-essential
apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base

* each of those lines was a separate command in terminal and needed to run their course of action. But know you had to do them to get all the right stuff in place to start @ step 1.

Step 3: In the terminal you have open copy and paste this line item:

/ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper

press enter key.

Here are the results:

Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.26.18.............................. ................................................................................ ................................................................................ ................................................................................ ................................................................................ ....
==================================================
 ATI Technologies Linux Driver Installer/Packager
==================================================
Generating package: Ubuntu/dapper
/tmp/fglrx.1G7boE /home/campjg/fglrx-install
Package /home/campjg/xorg-driver-fglrx_8.26.18-1_i386.deb has been successfully generated
Package /home/campjg/xorg-driver-fglrx-dev_8.26.18-1_i386.deb has been successfu lly generated
Package /home/campjg/fglrx-kernel-source_8.26.18-1_i386.deb has been successfull y generated
Package /home/campjg/fglrx-control_8.26.18-1_i386.deb has been successfully gene rated
Package /home/campjg/fglrx-sources_8.26.18-1_i386.deb has been successfully gene rated
/home/campjg/fglrx-install
Removing temporary directory: fglrx-install

Step 4: In the terminal you have open copy and paste this line item:

dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb

press enter key.

Here are the results:

(Reading database ... 106012 files and directories currently installed.)
Preparing to replace xorg-driver-fglrx 8.26.18-1 (using xorg-driver-fglrx_8.26.18-1_i386.deb) ...
Stopping atieventsd: done.
Unpacking replacement xorg-driver-fglrx ...
Setting up xorg-driver-fglrx (8.26.18-1) ...
Starting atieventsd: done.

Step 5: In the terminal you have open copy and paste this line item: 

dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb

press enter key.

Here are the results:

(Reading database ... 106012 files and directories currently installed.)
Preparing to replace fglrx-kernel-source 8.26.18-1 (using fglrx-kernel-source_8.26.18-1_i386.deb) ...
Unpacking replacement fglrx-kernel-source ...
Setting up fglrx-kernel-source (8.26.18-1) ...

Step 6: In the terminal you have open copy and paste this line item: 

dpkg -i fglrx-control_8.26.18-1_i386.deb

press enter key.

Here are the results:

(Reading database ... 106012 files and directories currently installed.)
Preparing to replace fglrx-control 8.26.18-1 (using fglrx-control_8.26.18-1_i386.deb) ...
Unpacking replacement fglrx-control ...
Setting up fglrx-control (8.26.18-1) ...

Step 7: In the terminal run each of these sequentially like you did for steps 4, 5, & 6:

Code: module-assistant prepare,update

See below with results:

root@UBUNTU606LTS:/home/campjg# module-assistant prepare,update
Getting source for kernel version: 2.6.15-25-k7
Kernel headers available in /usr/src/linux

Done!

Updated infos about 70 packages

Code: module-assistant build,install fglrx

See below with results:

root@UBUNTU606LTS:/home/campjg# module-assistant build,install fglrx
Extracting the package tarball, /usr/src/fglrx.tar.bz2, please wait...
Target package file /usr/src/fglrx-kernel-2.6.15-25-k7_8.26.18-1+2.6.15-25.43_i386.deb already exists, not rebuilding!
Version 8.26.18-1+2.6.15-25.43 of fglrx-kernel-2.6.15-25-k7 already installed, skipping.

Next terminal line of code to be copied and pasted: depmod

It takes a moment to run and simply has no output, but you know it's done when you get another command prompt in your terminal.

Step 8: Run these two lines of code:

Code: aticonfig --initial 

Results:

Found fglrx primary device section
Nothing to do, terminating.

Your's may have to take amoment to do waht it needs to do.

Code: aticonfig --overlay-type=Xv

Results:

Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-5

Again, your computer may need to take the necessary time to do the job it needs to do, but it is at this point you need to reboot and that is step 9.

Step 9: Reboot

Step 10: Check the results:

Code: fglrxinfo

Results: 

root@UBUNTU606LTS:~# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5879 (8.26.18)

---

### Post by jgcamp99 on 2006-06-29
If all went well, you should have ATi's Control placed under the:

Applications
Accessories
ATi Control

and this allows you to configure via the control panel.

---

### Post by Cyclohexane on 2006-06-29
That is exactly what I get.. save for the last thing.. no matter what I try, the Mesa drivers are always there...

And when I opened the ATi Control Panel, I still see Mesa in there..

---

### Post by jgcamp99 on 2006-06-29
Cyclohexane, if you used my method and are root, don't type sudo it's unnecessary !

---

### Post by Cyclohexane on 2006-06-29
I understand that.. No matter what I try, it still doesn't seem to recognize the new drivers, and go over the old drivers.. Do you think it has something to do with my xorg.conf? or do I have to take it off the Blacklist?

---

### Post by jgcamp99 on 2006-06-29
Hmmm. the only thing I can think of that was remotely different was that I got 8.25.18 on before 8.26.18. I know it would be a download, but perhaps downloading 8.25.18 and going thru it might get them on and then the update for 8.26.18 was a breeze. I didn't even uninstall 8.25.18.

I know I ran the 8.25.18 run program and didn't do the specific distro install. I got mesa like you did and then I ran the command to uninstall because it was an automatic installation.

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.26.18-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.26.18-inst.html)

If the ATI Proprietary Linux Driver was installed using either the Automatic or Custom options, then do the following:

   1. Launch the Terminal Application/Window and navigate to the /usr/share/fglrx folder.
   2. With super user permissions, enter the command "sh ./fglrx-uninstall.sh" 

You have now successfully uninstalled the ATI Linux Proprietary Driver.

Here is 8.25.18 archived:

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.25.18-x86.run)

---

### Post by jgcamp99 on 2006-06-29
Cyclo, I know I didn't do those sudo blacklist terminal commands, I never had old fglrx on my Ubuntu, and when I did the rm to remove that file in the instructions, it errored because there was no such file, once I got 8.25.18 on, I did go to that directory and manually put it in the trash. And when I went thru the process, the fglrx for 8.26.18 was in that directory. Do you have that file there ?

fglrx-kernel-2.6.15-25-k7_8.26.18-1+2.6.15-25.43_i386.deb

in /usr/src

Blacklist old fglrx module from linux-restricted-modules

Code:

sudo gedit /etc/default/linux-restricted-modules-common


DISABLED_MODULES to include fglrx
File: /etc/default/linux-restricted-modules-common

DISABLED_MODULES="fglrx"

---

### Post by Cyclohexane on 2006-06-29
[QUOTE=jgcamp99]Do you have that file there ?

fglrx-kernel-2.6.15-25-k7_8.26.18-1+2.6.15-25.43_i386.deb

in /usr/src

[/QUOTE]

Yes, I do..

---

### Post by Cyclohexane on 2006-06-29
Ok.. Well I think I have found the problem.. But I do not know how to fix it.. I cannot change the ati driver to fglrx because it doesn't see fglrx as a driver.. When I tell it to run from the driver fglrx, the x server doesn't load, and it gives me an error telling me that the driver fglrx does not exist..

---

### Post by apoclypse on 2006-06-29
in the command line type in lsmod | grep fglrx and if you see a result then atht means your module was loaded properly and it your xorg config that you need to be worried about. Otherwise this measn that module is either not loading or not installed correctly. i always suggest that you install the ones from the repos as for some reason compiling the drivers never works for me and i have to install them manually. If at all possible try dong an dpkg --purge fglrx and then sudo apt-get install fglrx or alternativaly yuo can do search for fglrx in synaptic and isnatll those drivers. If you ran aticonfig before then you should have a backup of your xorg.conf file it should called xorg.conf.200 something (the number are huge). Do a sudo mv xorg.conf.200 whatever the file name is xorg.conf (it would look like this sudo mv xorg.conf.20060529195851  xorg.conf) then again in the terminal do a sudo gedit xorg.conf. In the xorg just change Driver "ati" to "fglrx" quotes included. Save. the reboot. you should be fine after that. Other wise I think you might be doing something wrong along the way. The process should be really easy install fglrx from repos then change Driver from "ati" to "fglrx", thats it, thats all there is to it.

---

### Post by apoclypse on 2006-06-29
oh btw, you migh want to do a reinstall packages in synaptic for you restricted kernel modules since the 8.26.16 drivers if they installed (which I doubt) might have erased the old ones. Again do a lsmod | fglrx in the commandline first before doing anything to see if its running, if thats the case then you should skip the fglrx installation part and go straight to the xorg.conf part.

---

### Post by Cyclohexane on 2006-06-29
I think I found a big problem.. I tried installing the packages in Synaptic (lots easier), but when I got to fglrx-kernel-2.6.15-25-386, I got this:
```
Package fglrx-kernel-2.6.15-25-386 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded,
has been obsoleted or is not available with the contents of sources.list
```

Anyone know how to fix this?

---

### Post by jgcamp99 on 2006-06-29
You know, how much stuff do you have on Ubuntu ? This might be easier to remove Ubuntu completely and start from scratch, that way whatever is or isn't there can be put there cleanly. Rather than fighting the battle like we have, a clean install and drivers going on before anything else might get you the clean working installation. I know once the drivers took and installed, the upgrade/update was a smooth transition.

---

### Post by Cyclohexane on 2006-06-29
well.. I might reinstall Ubuntu.. It wouldn't be too much of a hassle.. But I still want to keep it as a last resort..

In fact.. I think i'm going to do that.. Thanks for all your help everybody..

---

### Post by jgcamp99 on 2006-06-29
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "IBM G97"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver      "ati"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor    "IBM G97"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

---

### Post by jgcamp99 on 2006-06-29
And the original xorg.conf

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Driver		"ati"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"IBM G97"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV350 AR [Radeon 9600 XT]"
	Monitor		"IBM G97"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
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

---

### Post by CapPicard on 2006-06-29
This is very frustrating.  I'm trying to get mine to work, but both monitors go out of sync.  Just trying to clone them... I'm having to use the ati drivers. The fglrx one is just ticking me off!

This is my xorg.conf file.

I have an Radeon 9600.

---

