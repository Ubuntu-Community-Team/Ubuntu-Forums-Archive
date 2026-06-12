---
title: "[SOLVED] Intel Graphics Media Accelerator 900"
date: 2007-08-15
forum: Dell  Ubuntu Support
---

### Post by Sneo on 2007-08-15
Hey, 
Anyone know about Getting GLX to work correctly with Intel onboard graphics chipsets - specifically, "Intel Graphics Media Accelerator 900".
Running a Dell Dimension 3100 with Ubuntu Feisty trying to play Defcon and was told I needed to get GLX to work properly first.

Help appreciated!

---

### Post by dougfractal on 2007-08-15
[http://scotu.netsons.org/blog/index.php/2007/07/08/how-to-get-your-intel-graphics-to-work-at-the-best-with-ubuntu-linux-feisty-704/](http://scotu.netsons.org/blog/index.php/2007/07/08/how-to-get-your-intel-graphics-to-work-at-the-best-with-ubuntu-linux-feisty-704/)
How to get your Intel graphics to work at the best with Ubuntu Linux (Feisty 7.04)
> 
Jul 8, 2007 in English, How-to, Open Source & Free Software, GNU/Linux

IntelThe first thing you need to know about your Intel Graphics Media Accelerator is that it rocks: it heats your pc less than any other video chipset and it uses less energy than any other chipset: in return you get not only a very good graphic result (for general uses like compiz and some other 3d apps) but it also comes with OPENSOURCE DRIVERS. That&#8217;s cool, right?

You can run your desktop at full resolution, you can run 3d applications all without needing to install propertary software on your machine (as for Nvidia or ATI drivers).

This will work if you have an Intel Graphic Media Accelerator (GMA) 800 and 900 series

Now let&#8217;s install everything you need:

   1. install 915resolution giving this command in the terminal:

    [QUOTE]sudo apt-get install 915resolution

And that&#8217;s all&#8230; restarting the X server (or rebooting the pc) is sufficient to be able to change to the resolution you prefer just opening (for GNOME) System> Preferences> Resolution[/QUOTE]

---

### Post by sciurus on 2007-08-16
Does it think it's working?

```
glxinfo | grep direct
```

Are you loading the glx module for X?

```
grep glx /etc/X11/xorg.conf 
```

What video driver are you using?

```
grep Driver /etc/X11/xorg.conf
```

---

### Post by Sneo on 2007-08-16
Thanks for the swift replies, really appreciated!

@dougfractal: Did that, still doesn't work.

@scirus:
```

sean@sean-desktop:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```
```

sean@sean-desktop:~$ grep glx /etc/X11/xorg.conf
        Load    "glx"

```

```
sean@sean-desktop:~$ grep Driver /etc/X11/xorg.conf
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "i810"
```
Any ideas?

---

### Post by Artemis3 on 2007-08-16
```
apt-get install xserver-xorg-video-intel
```

Do not use compiz while watching videos until they fix that silly bug...

---

### Post by Sneo on 2007-08-16
Still nothing.

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Well apart from the fact that my usual account now can't load as its gone out of screen resoloution!

---

### Post by dougfractal on 2007-08-16
> nano /etc/X11/xorg.conf

change Driver          "i810"
to 
> Driver  "intel"

if still a problem  Driver  "vesa"  # recovory mode


can post Section "Module"

---

### Post by Sneo on 2007-08-16
Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

> change Driver "i810"
to
Quote:
Driver "intel"
if still a problem Driver "vesa" # recovory mode

The Driver is "intel" already.. Got my account back! What next? 

Thanks again to everyone thats helping! Really appreciate it!

---

### Post by walkerk on 2007-08-16
> **Artemis3 said:**
> ```
apt-get install xserver-xorg-video-intel
```

Do not use compiz while watching videos until they fix that silly bug...

What silly bug? You can change the video output in most media players to x11 which will work while running compiz. There is still a lot of improvement for video with compiz w/ Intel GM video but it does work..

---

### Post by Sneo on 2007-08-16
> **walkerk said:**
> What silly bug? You can change the video output in most media players to x11 which will work while running compiz. There is still a lot of improvement for video with compiz w/ Intel GM video but it does work..

Well I'm not running compiz, I'm trying to get a game working.. any ideas?

---

### Post by dougfractal on 2007-08-16
try the "proposed" binary

[https://launchpad.net/ubuntu/feisty/i386/xserver-xorg-video-intel/2:1.9.94-1ubuntu4](https://launchpad.net/ubuntu/feisty/i386/xserver-xorg-video-intel/2:1.9.94-1ubuntu4)

or try the gusty version, it would require updating all xorg.

I think the problem may be corrupted mesa. I know this happens with flgrx.  
It might be an idea to expirement from liveCD (do you have enough ram?) cos I thought it should work straight out.


try this , I'm really scrapping ideas

> sudo apt-get install --reinstall  xserver-xorg-video-intel
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri # 

---

### Post by Sneo on 2007-08-16
> **dougfractal said:**
> try the "proposed" binary

[https://launchpad.net/ubuntu/feisty/i386/xserver-xorg-video-intel/2:1.9.94-1ubuntu4](https://launchpad.net/ubuntu/feisty/i386/xserver-xorg-video-intel/2:1.9.94-1ubuntu4)

or try the gusty version, it would require updating all xorg.

I think the problem may be corrupted mesa. I know this happens with flgrx.  
It might be an idea to expirement from liveCD (do you have enough ram?) cos I thought it should work straight out.

I'll add a clean up and start again in a bit.

ok, so wait. Try gusty? or try this? 

Tried that link. Still the same! I have a gig of ram.. livecd? What should i test from a livecd?

Did the reinstallations. Again nothing!

---

### Post by dougfractal on 2007-08-16
I've been looking around the intel site.
[http://www.intellinuxgraphics.org/documentation.html](http://www.intellinuxgraphics.org/documentation.html)


can you  driver "intel"
> Well apart from the fact that my usual account now can't load as its gone out of screen resoloution!
 [http://ubuntuswitch.wordpress.com/tag/feisty/](http://ubuntuswitch.wordpress.com/tag/feisty/)
 there's a whole bit on **915resolution** from CL


lspci -nn
glxinfo
glxgears


this guy had it running on breezy, but so much has changed from then
[http://jaganath.wordpress.com/2006/06/25/ubuntu-install-log-4-awesome-graphics-on-the-linux-desktop-using-aiglx-and-compiz-better-than-vista-and-os-x/](http://jaganath.wordpress.com/2006/06/25/ubuntu-install-log-4-awesome-graphics-on-the-linux-desktop-using-aiglx-and-compiz-better-than-vista-and-os-x/)

> Tried that link. Still the same! I have a gig of ram.. livecd? What should i test from a livecd?  

From the LiveCD you can download, install, restart X.  (I've run nvidia beryl from LiveCD).  You just need enough ram to hold all the changes (or a special format usbstick).  

It might be worth testing a live Gusty.   As that has even newer intel drivers. It looks as if they are tring to merge i810 and intel.  

Were all the xorg changes made during this thread or have there been other goes?

---

### Post by Sneo on 2007-08-16
> 
[http://ubuntuswitch.wordpress.com/tag/feisty/](http://ubuntuswitch.wordpress.com/tag/feisty/)
there's a whole bit on 915resolution from CL


lspci -nn
glxinfo
glxgears


this guy had it running on breezy, but so much has changed from then
[http://jaganath.wordpress.com/2006/0...ista-and-os-x/](http://jaganath.wordpress.com/2006/0...ista-and-os-x/)


I have my screen resoloution sorted! 

> 
From the LiveCD you can download, install, restart X. (I've run nvidia beryl from LiveCD). You just need enough ram to hold all the changes (or a special format usbstick).

It might be worth testing a live Gusty. As that has even newer intel drivers. It looks as if they are tring to merge i810 and intel.

Were all the xorg changes made during this thread or have there been other goes?

I'll give a live cd of Gusty a shot. ! :) Thanks

---

### Post by dougfractal on 2007-08-16
one more go ;)
> Well apart from the fact that my usual account now can't load as its gone out of screen resoloution!
I think it might be almost  there.


> 
sudo /etc/init.d/gdm stop   #  stop X
sudo 915resolution 3c 1400 1050
sudo /etc/init.d/gdm start   # 
 

**Note**: You should call **915resolution -l** before and replace 3c with a resolution you will not use.

go on just one more go.

---

### Post by Sneo on 2007-08-17
> **dougfractal said:**
> one more go ;)

I think it might be almost  there.




**Note**: You should call **915resolution -l** before and replace 3c with a resolution you will not use.

go on just one more go.

Done, :( Still nothing.

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```
Anyway I can make this easier for you? Remote desktop??

---

### Post by dougfractal on 2007-08-17
> Anyway I can make this easier for you? Remote desktop??

sent private message.

---

### Post by Sneo on 2007-08-17
replied! :)

---

### Post by dougfractal on 2007-08-17
**system spec grabber**

paste this in terminal
```
mkdir ~/Xinfo
cd ~/Xinfo
echo 'touch X.info # create file
lsb_release -d > X.info # version
uname -r >> X.info # kernel
lspci -nn >> X.info # list hardware
glxinfo | head -4 >> X.info
script -c " glxgears &  sleep 11 ;  pkill -15 glxgears"   
cat typescript | grep FPS >> X.info
cp /etc/X11/xorg.conf ./   # graphics file
cp /var/log/Xorg.0.log ./
cp /etc/modprobe.d/blacklist ./
aptitude search ~imesa ~ixorg  ~idbus ~icompiz -F "%20p %10v %10V %20d" > installed.txt
tar -czf xinfo.tar.gz X.info xorg.conf Xorg.0.log installed.txt blacklist ' | tee xinfo.sh
sed -i '1i#!/bin/bash' xinfo.sh
chmod a+x xinfo.sh
./xinfo.sh
echo -e "\nplease attach $PWD/**xinfo.tar.gz**"

```
please attach **xinfo.tar.gz**

---

### Post by Sneo on 2007-08-17
It just made xinfo.sh in the folder.. 

```
#!/bin/bash
touch X.info # create file
lsb_release -d > X.info # version
uname -r >> X.info # kernel
lspci -nn >> X.info # list hardware
glxinfo | head -4 >> X.info
script -c " glxgears &  sleep 11 ;  pkill -15 glxgears"   
cat typescript | grep FPS >> X.info
cp /etc/X11/xorg.conf ./   # graphics file
cp /var/log/Xorg.0.log ./
cp /etc/modprobe.d/blacklist ./
aptitude search ~imesa ~ixorg  ~idbus ~icompiz -F "%20p %10v %10V %20d" > installed.txt
tar -czf xinfo.tar.gz X.info xorg.conf Xorg.0.log installed.txt blacklist 
```

By running that I got this file:
X.info

```
Description:	Ubuntu 7.04
2.6.20-16-386
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d4)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 04)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller [8086:2652] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
03:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 04)
name of display: :0.0

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
```

---

### Post by dougfractal on 2007-08-17
chmod a+x xinfo.sh
./xinfo.sh

---

### Post by Sneo on 2007-08-17
Perfect! 

File attached!

---

### Post by dougfractal on 2007-08-17
Can you post your /etc/apt/sources.list   as it looks as if your missing the new CF stuff

this is JesseEklund xorg.conf it should work on yours, but will need tweaking  but he's getting dri and 700fps
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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

---

### Post by Sneo on 2007-08-17
```

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb http://ie.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ie.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ie.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://ie.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://ie.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ie.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://ie.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://download.introversion.co.uk/defcon/linux/contrib/ubuntu-feisty/ feisty main
deb     http://mirror.noreply.org/pub/tor feisty main
deb-src http://mirror.noreply.org/pub/tor feisty main
```

---

### Post by dougfractal on 2007-08-17
update repos

from [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

```
sudo apt-get --purge remove compiz* libcompizconfig*
```


First, we need to add a third party repository to your** sudo gedit  /etc/apt/sources.list** . (Help for this available at AddingRepositoriesHowto)

```
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
``` 

After adding the repository, we need to update our repositories and install it.

```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager
```

---

### Post by Sneo on 2007-08-18
Ok, replaced my xorg.conf like you said and did the compiz thing..

Still

sean@seanland:~$ glxinfo | grep renderingXlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

And now I have update manager asking me to update compiz-core. But even if I do, it seems to want the same update again and again again. 

Do you have any other ideas? Again feel free to use the way in I gave you, its still open and the stuff is the same. If lets say you had root access would it speed things up?

---

### Post by dougfractal on 2007-08-18
the problem was you had tried to install nvidia drivers which corrupted the intel glx.
[COLOR="Silver"]
> so I
sudo apt-get remove nvidia-glx
sudo apt-get install --reinstall xserver-xorg-video-intel[/COLOR]

should be all done

restartX

---

### Post by dougfractal on 2007-08-18
> Got it perfect! Thanks so much! 

1)  reinstall your old xorg.conf   
```
sudo cp /etc/X11/xorg.conf   /etc/X11/xorg.conf.JesseEklund
sudo cp  /home/s*/Xinfo/xorg.conf  /etc/X11/xorg.conf
```

restart X

then can you post me *xinfo.tar.gz  (new version)


```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by Sneo on 2007-08-20
Nice gears script. 

File attached!

---

### Post by raghuramos1987 on 2007-09-06
guys...i'm havin the same card...did everythin discussed in this thread..still its not wrkin...i'm gettin this error when i run the xinfo.sh script

ros@ros-desktop:~/Xinfo$ ./xinfo.sh
Enter your Ubuntu name(no spaces):
Feisty
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Script started, file is typescript
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
Script done, file is typescript
Description:    Ubuntu 7.04
2.6.20-16-generic
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz         : 3000.000
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz         : 3000.000
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 0e)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 0e)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d4)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 04)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
01:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
X.Org version: 7.2.0
  dimensions:    1024x768 pixels (302x230 millimeters)
  depth of root window:    24 planes

Created /home/ros/Xinfo/Feistyxinfo.tar.gz
ros@ros-desktop:~/Xinfo$

---

### Post by dougfractal on 2007-09-07
The script is working its just reporting that you have GLX problems (as you know)  
just attach the /home/ros/Xinfo/**Feistyxinfo.tar.gz**

This info is fine but I do have an improved script [http://ubuntuforums.org/showpost.php?p=3212515&postcount=28](http://ubuntuforums.org/showpost.php?p=3212515&postcount=28)




[B]
This might help[/B]
> sudo apt-get remove nvidia-glx
sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-dri libgl1-mesa-glx

restart X

---

### Post by raghuramos1987 on 2007-09-10
this is the file /home/ros/Xinfo/Feistyxinfo.tar.gz and i tried the cmds...didnt wrk :(

---

### Post by dougfractal on 2007-09-11
Hi raghuramos1987

putting this on a solved thread might mean you wont get much help!

this might help 
> #sudo apt-get install --reinstall libgl1-mesa-swx11   # i'm unsure about this


looking at sneo's installed files  [http://ubuntuforums.org/showpost.php?p=3220998&postcount=29](http://ubuntuforums.org/showpost.php?p=3220998&postcount=29)
> sudo apt-get remove libosmesa6*
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx


You've got a mixed up sources.list lots of  dapper feisty stuff. clean it up.
or use sneo's sources.list
> sudo cp /etc/apt/get/sources.list /etc/apt/get/sources.list.old
sudo cp <MY NEW LIST> /etc/apt/get/sources.list
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

REBOOT

then can you post me *xinfo.tar.gz  (new version)


```
mkdir ~/Xinfo
cd ~/Xinfo
wget -O xinfo.sh  http://fractaldimension.org.uk/ubuntu/xinfo.txt
chmod a+x ./xinfo.sh
./xinfo.sh
```


please attach the ***xinfo.tar.gz**

view script
 [http://fractaldimension.org.uk/ubuntu/xinfo.txt](http://fractaldimension.org.uk/ubuntu/xinfo.txt)

---

### Post by raghuramos1987 on 2007-09-22
about the mix up of sources.list u're rite...i'm not at my actual comp now...will try replacin sources.list and the rest of the stuff u said and get back....thanks a lot...

---

### Post by raghuramos1987 on 2007-09-24
i did wat u said...this is the file...and i replaced my sources.list also

---

### Post by raghuramos1987 on 2007-09-25
sorry...that was the wrong file...this is the correct one

---

### Post by dougfractal on 2007-09-25
from Xorg.0.log
> (II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
(II) Loading extension GLX
.
.
.
(EE) intel(0): [dri] I830CheckDRIAvailable failed: glx not loaded

try this
> sudo apt-get remove libosmesa6 libosmesa6-dev
sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa xserver-xorg-video-intel

restartx and good luck

**check**
> grep EE /var/log/Xorg.0.log
grep NVIDIA /var/log/Xorg.0.log

---

### Post by raghuramos1987 on 2007-10-23
hey....sorry...you had asked me to post on a separate thread so thought u wud reply there...i tried the last one u said...but now i have upgraded to gutsy and no problems thr but same prob with the display...compiz doesn wrk...this is the o/p og glxinfo...help! :(

ros@ros-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.2
GLX extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGI_swap_control, 
    GLX_SGIX_fbconfig, GLX_ARB_get_proc_address
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:
    GL_ARB_depth_texture, GL_ARB_fragment_program, GL_ARB_imaging, 
    GL_ARB_multitexture, GL_ARB_point_parameters, GL_ARB_shadow, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_vertex_program, GL_ARB_window_pos, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texture3D, GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add, 
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_vertex_array, 
    GL_IBM_texture_mirrored_repeat, GL_NV_blend_square, 
    GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x2b 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2f 24 dc  0 32  0 r  y  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x30 24 dc  0 32  0 r  .  .  8  8  8  8  0  0  0 16 16 16 16  0 0 Slow
0x31 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x32 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 Slow
0x5b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

---

### Post by dougfractal on 2007-10-25
can you post your latest xinfo.tar.gz   as it shows me loads of info.

You still seem to have nvidia glx contamination.

---

### Post by raghuramos1987 on 2007-10-28
this is the new file....

---

### Post by dougfractal on 2007-10-28
Sorry to say I don't know the answer.  everything should be ok
what is strange is that you xorg.0.log has
> (II) intel(0): direct rendering: Enabled
...
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0

and 760fps isn't so bad.
whats the output from **compiz --replace  &**

---

### Post by raghuramos1987 on 2007-10-29
ros@ros-desktop:~$ compiz --replace &
[1] 8957
ros@ros-desktop:~$ Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 0e) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

this is the output..but wat i don get is that i have the same chip as specified in this thread :(

---

