---
title: "I just want to make the Intel 945gm work with Beryl"
date: 2007-07-12
forum: Desktop Effects &amp; Customization
---

### Post by duydaniel on 2007-07-12
I am sorry. But I have used windows since 3.11 -> Vista and finally been convinced that Windows sucks.

I switch to Linux... my Laptop is Dell 6400 with Intel 945GM graphic card.

I did my best on trying google to make it work with Beryl... but it can't. There are many posts show how to do it... but I still not be able to do it. Probably, they are complicated and assumed pre-knowledge about Linux. I was so painful to look for drivers to me. It took me days to make the Dell wireless work, but I stuck with the graphic card now.

I am new to Linux and only know how to copy and paste commands into terminal.
I would appreciate if you have something "easy to understand" guide to install the Intel945GM correctly... making it works with Beryl.

---

### Post by Wiebelhaus on 2007-07-12
fyi dude , using that kind of language will not get you attention here , beryl isn't a necessity , if your onboard video isn't capable of running high end graphics such as beryl there's nothing you can copy & paste that'll fix that.


But , it does look like people are getting it to work:
[http://yogharp.wordpress.com/2006/12/19/ubuntu-edgy-on-intel-945gm-graphics-wide-screen-lcd-notebooks/](http://yogharp.wordpress.com/2006/12/19/ubuntu-edgy-on-intel-945gm-graphics-wide-screen-lcd-notebooks/)
[http://www.youtube.com/watch?v=VxFKp8EBdBo](http://www.youtube.com/watch?v=VxFKp8EBdBo)

---

### Post by duydaniel on 2007-07-12
> **sx66gns said:**
> fyi dude , using that kind of language will not get you attention here , beryl isn't a necessity , if your onboard video isn't capable of running high end graphics such as beryl there's nothing you can copy & paste that'll fix that.


But , it does look like people are getting it to work:
[http://yogharp.wordpress.com/2006/12/19/ubuntu-edgy-on-intel-945gm-graphics-wide-screen-lcd-notebooks/](http://yogharp.wordpress.com/2006/12/19/ubuntu-edgy-on-intel-945gm-graphics-wide-screen-lcd-notebooks/)
[http://www.youtube.com/watch?v=VxFKp8EBdBo](http://www.youtube.com/watch?v=VxFKp8EBdBo)

I am using Ubuntu 7.04... will it applicable?

---

### Post by kavon89 on 2007-07-12
I don't know why you expect the cool Beryl effects with your integrated Intel graphics display. It's not happening, especially for integrated display unless you want your desktop to become a sideshow.  Come back with an Nvidia card or a good ATI card and try Beryl.

---

### Post by duydaniel on 2007-07-12
> **kavon89 said:**
> I don't know why you expect the cool Beryl effects with your integrated Intel graphics display. It's not happening, especially for integrated display unless you want your desktop to become a sideshow.  Come back with an Nvidia card or a good ATI card and try Beryl.

I have not tested many games on I945GM... but I once ran Command and Conquer General on my Laptop (windows XP) with highest setting... it ran quite smooth. I also used to make the beryl worked once... then it gone... I had no idea... I am absolute novice in Linux.

P.S. My laptop is Core 2 Duo, 2GB Ram and 128MB shared with i945GM... I will try to google more...  isn't it true that ppl switch to Linux since they hate the "upgradism" from Bill Gate. Even if my lap can run Vista well, it will be even faster in Linux... Vista sucks

---

### Post by AndrewGene on 2007-07-12
I am running compiz fusion (After running beryl for months) on an intel integrated graphics system.  I have a core duo (not core 2 duo) and 1 GB of ram.  It runs just fine.  I have the cube/expo/transparencies....everything.

---

### Post by duydaniel on 2007-07-12
> **AndrewGene said:**
> I am running compiz fusion (After running beryl for months) on an intel integrated graphics system.  I have a core duo (not core 2 duo) and 1 GB of ram.  It runs just fine.  I have the cube/expo/transparencies....everything.

How did you make it work sir?
I am still on google for it... the chess game even can't run as 3D.

P.S. There is not much differ from Core Duo and Core 2 Duo if they are close at clock speed.

---

### Post by duydaniel on 2007-07-12
Now it can run 3D mode in chess by the post from:
[http://www.mikesplanet.net/2007/03/turning-on-3d-chessboard-in-feisty/](http://www.mikesplanet.net/2007/03/turning-on-3d-chessboard-in-feisty/)

But, it still not be able to run Beryl (I don't know what compiz is yet), and when I enable "Desktop Effects" the 3D cube does not work... every windows title bars disappeared... though I still can grab them... but they are invisible.

I don't know if you have been such problem? I am an idiot in Linux so would appreciate if someone give me a step by step "copy and paste" commands.

---

### Post by AndrewGene on 2007-07-12
No there is not much different.  The ram is gonna make more of a difference.  I am looking for the exact thread that I got the how-to from.  I thought I had it bookmarked.

P.S. The chess game is not dependent on beryl.  It sucks in 3D anyways--well at least on our graphics card. It isn't even really playable.

---

### Post by AndrewGene on 2007-07-12
Well, first and foremost, would you want to install compiz fusion instead of beryl?  Compiz and beryl merged, hence, compiz FUSION.  It wil actually continue to be supported--unlike beryl.  I find it to be more stable.

---

### Post by duydaniel on 2007-07-12
> **AndrewGene said:**
> Well, first and foremost, would you want to install compiz fusion instead of beryl?  Compiz and beryl merged, hence, compiz FUSION.  It wil actually continue to be supported--unlike beryl.  I find it to be more stable.

sure sir... it will be great.
My problem is to find out how to install the 945GM correctly... I don't know but in my windows' experiences, if 3D can't be run, that probably means your graphic card is not installed appropriately. I don't know if that is true with Linux.

let me read the sticky thread to see... it also be great if you give me the instruction that worked for you since we have the same card.

---

### Post by arsenic23 on 2007-07-12
First off, I wouldn't worry about your video drives, they should just work.  I'm going to asume that Beryl should also work for you, seeing as I have it running on an Intell 855GM without any kind of slowdown.

First run glxgears so we can make sure something isn't wrong with your 3d.  
The other thing is, when you installed beryl originally did you add any new repositories?  
What is the results of:
```
cat /etc/apt/sources.list
```?

---

### Post by duydaniel on 2007-07-12
> **arsenic23 said:**
> First off, I wouldn't worry about your video drives, they should just work.  I'm going to asume that Beryl should also work for you, seeing as I have it running on an Intell 855GM without any kind of slowdown.

First run glxgears so we can make sure something isn't wrong with your 3d.  
The other thing is, when you installed beryl originally did you add any new repositories?  
What is the results of:
```
cat /etc/apt/sources.list
```?

Hi sir... after the code:

daniel@daniel-laptop:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports universe main multiverse restricted
daniel@daniel-laptop:~$

P.S. I don't know how to "run glxgears"

---

### Post by duydaniel on 2007-07-12
Here is the content of the file xorg.conf

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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Generic Video Card"
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
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection



I don't know if that would help

---

### Post by arsenic23 on 2007-07-12
Ok, to run glxgears, you just type *glxgear* into the terminal.  It'll show little 3d gears running and every few seconds output your fps into the terminal window you ran it in.  It's the best way (I know of) to make sure your rending 3d correctly.

I think the best chance to get beryl working would be to install the version in the official repositories.  So you should either remove the [COLOR="Gray"]deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main[/COLOR] line from your sources.list, or replace it completely.  To edit it just type 
```
gksudo gedit /etc/apt/sources.lst
```
into your terminal.

The easiest thing to do would be to just delete the contents of your sources.list and replace them with:
```
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-security main universe multiverse restricted

deb http://archive.canonical.com/ubuntu/ edgy-commercial main
deb http://archive.canonical.com/ubuntu/ feisty-commercial main
```

Now after you do that, and asuming your glxgear ran, we can start removing the version of beryl you currantly have installed.  Type this into your terminal to remove beryl:
```
sudo apt-get remove beryl beryl-core emerald beryl-manager beryl-pluggins beryl-pluggins-data beryl-settings emerald-themes libemeraldengine0  libberyldecoration0 libberylsettings0 libemeraldengine0 && sudo apt-get clean
```

If there are errors here, stop.  Don't do anything else and post back here - if not keep going. Now to make sure everything installed is up to date based on the new repository setup type this into your terminal:
```
sudo apt-get update && sudo apt-get upgrade
```

Now to install beryl from the ubuntu repository type:
```
sudo aptitude install bery beryl-manager emerald emerald-themes
```

After this completes ( asuming no errors along the way ), beryl should start by typing into your terminal:
```
beryl-manager &
```

If that's good then you can just add [COLOR="DimGray"]beryl-manager[/COLOR] to your startup under Syster>>Preferences>>Sessions

---

### Post by duydaniel on 2007-07-12
> **arsenic23 said:**
> Ok, to run glxgears, you just type *glxgear* into the terminal.  It'll show little 3d gears running and every few seconds output your fps into the terminal window you ran it in.  It's the best way (I know of) to make sure your rending 3d correctly.

I think the best chance to get beryl working would be to install the version in the official repositories.  So you should either remove the [COLOR="Gray"]deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main[/COLOR] line from your sources.list, or replace it completely.  To edit it just type 
```
gksudo gedit /etc/apt/sources.lst
```
into your terminal.

The easiest thing to do would be to just delete the contents of your sources.list and replace them with:
```
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main universe multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ feisty-security main universe multiverse restricted

deb http://archive.canonical.com/ubuntu/ edgy-commercial main
deb http://archive.canonical.com/ubuntu/ feisty-commercial main
```

Now after you do that, and asuming your glxgear ran, we can start removing the version of beryl you currantly have installed.  Type this into your terminal to remove beryl:
```
sudo apt-get remove beryl beryl-core emerald beryl-manager beryl-pluggins beryl-pluggins-data beryl-settings emerald-themes libemeraldengine0  libberyldecoration0 libberylsettings0 libemeraldengine0 && sudo apt-get clean
```

If there are errors here, stop.  Don't do anything else and post back here 

Thanks sir... here is the error after I typed the code:

```
daniel@daniel-laptop:~$ sudo apt-get remove beryl beryl-core emerald beryl-manager beryl-pluggins beryl-pluggins-data beryl-settings emerald-themes libemeraldengine0  libberyldecoration0 libberylsettings0 libemeraldengine0 && sudo apt-get clean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl-pluggins
daniel@daniel-laptop:~$
```

---

### Post by eentonig on 2007-07-12
I would advice NOT to install Beryl. But go for Compiz Fusion.

It works a lot better on low end GPU's like the intel family.

[Use this thread to install Compiz Fusion]("http://ubuntuforums.org/showthread.php?t=481314v")

---

### Post by duydaniel on 2007-07-12
> **eentonig said:**
> I would advice NOT to install Beryl. But go for Compiz Fusion.

It works a lot better on low end GPU's like the intel family.

[Use this thread to install Compiz Fusion]("http://ubuntuforums.org/showthread.php?t=481314v")

Sure sir.
But I don't know much about Ubuntu as the thread read "not for beginner" and I am working on arsenic23's help. It is not a good idea to follow 2 instructions at once... it probably mess up the computer...  :KS

Btw, the glxgears runs fine... but 

```
daniel@daniel-laptop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  35
  Current serial number in output stream:  35
daniel@daniel-laptop:~$
```

---

### Post by tgm4883 on 2007-07-12
> **kavon89 said:**
> I don't know why you expect the cool Beryl effects with your integrated Intel graphics display. It's not happening, especially for integrated display unless you want your desktop to become a sideshow.  Come back with an Nvidia card or a good ATI card and try Beryl.

Unless you tried it, or KNOW that it doesn't work......  Cause compiz fusion works just fine on my Dell E1505/6400 with Intel 945GM.

> **duydaniel said:**
> How did you make it work sir?
I am still on google for it... the chess game even can't run as 3D.

P.S. There is not much differ from Core Duo and Core 2 Duo if they are close at clock speed.

The difference between a Core Duo and a Core 2 Duo is that the Core 2 Duo is 64-bit

> **duydaniel said:**
> Sure sir.
But I don't know much about Ubuntu as the thread read "not for beginner" and I am working on arsenic23's help. It is not a good idea to follow 2 instructions at once... it probably mess up the computer...  :KS

Btw, the glxgears runs fine... but 

```
daniel@daniel-laptop:~$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  35
  Current serial number in output stream:  35
daniel@daniel-laptop:~$
```

Looks like we have the same laptop with the same video card.  Good news then cause Compiz fusion works great on mine (along with Avant Window Navigator and Screenlets if you want).

It doesn't look like you have the proper video driver loaded though.  It might be, but lets just be sure.  I would assume that your screen looks stretched horizontally?  You need to "sudo apt-get install 915resolution" if it says already installed, then your fine.  If it installs it (or asks you to install it, press Y), the reboot when it's finished installing.

The guide posted earlier [http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion]("http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion") is the correct guide.  The not for beginners was saying that the guide wasn't for beginners (as most guides are for beginners).  What it was warning you about is that Compiz Fusion is still under development and is not stable yet.  There are times that I have had to restart X a few times to get this to work.  Basically, it may break and you can't boot into gnome (or KDE).

That is the guide I followed, and although not a newbie, it seemed pretty straight forward.

---

### Post by arsenic23 on 2007-07-12
> **duydaniel said:**
> Thanks sir... here is the error after I typed the code:

```
daniel@daniel-laptop:~$ sudo apt-get remove beryl beryl-core emerald beryl-manager beryl-pluggins beryl-pluggins-data beryl-settings emerald-themes libemeraldengine0  libberyldecoration0 libberylsettings0 libemeraldengine0 && sudo apt-get clean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl-pluggins
daniel@daniel-laptop:~$
```

Ok just remove bery-pluggins from that command and do it again.  If it can't find another one, remove that one and do it again, untill you it runs without errors.  If in the very end this does not work for you, you can always come back to this remove command, run it again and try another method.

---

### Post by AndrewGene on 2007-07-12
Yes, remove beryl with the ways mentioned above.  Before you install compiz fusion you will also need a window decorator (the borders for the windows) so in the terminal type:
sudo aptitude install emerald 
***It is a good idea to use "aptitude" instead of "apt-get" because if you ever have to remove something i.e. "apt-get remove"/"aptitude remove" then aptitude will remove all of the packages that were installed with the main file (dependencies) and apt-get will only uninstall the main program--not the dependencies*** Just FYI since you are new to linux.

My video card was set up straiight out of the box so I guess I was just lucky.
If you need help with anything else, post up.

tgm4883 gave you the right link.  On my system when you press alt-f2 (after everything is installed and updated) you type "compiz --replace -c emerald &"  

If you want compiz fusion (cf) to start at startup then that can be done also.

---

### Post by duydaniel on 2007-07-12
I don't know if I have the correct driver... 

```
daniel@daniel-laptop:~$ sudo apt-get install 915resolution
Reading package lists... Done
Building dependency tree       
Reading state information... Done
915resolution is already the newest version.
The following packages were automatically installed and are no longer required:
  matchbox-window-manager matchbox-panel matchbox-panel-manager tofrodos
  matchbox-common icedax libmatchbox1 python-pysqlite2 libsdl-mixer1.2
  libgcompris-1-0 gcompris-data beryl-plugins-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
daniel@daniel-laptop:~$ 
```

the desktop looks stretch horizontally. When I go to Screen Resolution, I found 
1280x800
1280x768
1024x768
800x600
1280x1280

Then, I try to enable "Desktop Effects" the following error appear:
"Desktop effects could not be be enabled"

Ms. Beryl seems to be gone since I could not find her in the Desktop search.
What should I do?

---

### Post by duydaniel on 2007-07-12
I should give up on that things...
since windows DOS -> 3.11 -> Vista... I never have such tough time.:(

---

### Post by sneax on 2007-07-12
> **kavon89 said:**
> I don't know why you expect the cool Beryl effects with your integrated Intel graphics display. It's not happening, especially for integrated display unless you want your desktop to become a sideshow.  Come back with an Nvidia card or a good ATI card and try Beryl.

sorry but you are not very helpful, i have intel intergated graphics 855gme and i got beryl running with different distro's in 32bit will all the transparancy and cube effects

even blurr works! but it makes everything too slow for desktop

what i always did was first test whether my hardware graphics were detected, for that i type this in a console:
glxgears
with the standards settings on 32bit it should give you about 1000fps or more with your 945 (i get 800fps)

if you get much less (like 100 or so) then you first need to find on how to make 'direct rendering' to work

then after that you need to install beryl using aiglx (and nog XGL) i don't really know the difference but i know that for intel cards aiglx is MUCH better and faster

---

### Post by arsenic23 on 2007-07-12
> **duydaniel said:**
> I should give up on that things...
since windows DOS -> 3.11 -> Vista... I never have such tough time.:(

Well, yeah, but did you ever try to install an alternitive window manager in Windows ? :)

Something interesting you might try:  If you boot the ubuntu live CD, will desktop effects work under it?

---

### Post by duydaniel on 2007-07-12
> **sneax said:**
> sorry but you are not very helpful, i have intel intergated graphics 855gme and i got beryl running with different distro's in 32bit will all the transparancy and cube effects

even blurr works! but it makes everything too slow for desktop

what i always did was first test whether my hardware graphics were detected, for that i type this in a console:
glxgears
with the standards settings on 32bit it should give you about 1000fps or more with your 945 (i get 800fps)

if you get much less (like 100 or so) then you first need to find on how to make 'direct rendering' to work

then after that you need to install beryl using aiglx (and nog XGL) i don't really know the difference but i know that for intel cards aiglx is MUCH better and faster

I don't know if I am in 32 bit... my screen resolution is 1280x800
Here is the result:

```
daniel@daniel-laptop:~$ glxgears
4671 frames in 5.1 seconds = 920.177 FPS
4486 frames in 5.1 seconds = 874.089 FPS
4640 frames in 5.0 seconds = 924.643 FPS
4740 frames in 5.1 seconds = 925.000 FPS
4700 frames in 5.1 seconds = 925.991 FPS
4727 frames in 5.1 seconds = 930.572 FPS
4700 frames in 5.1 seconds = 928.588 FPS
4633 frames in 5.0 seconds = 924.798 FPS
4887 frames in 5.0 seconds = 972.141 FPS
5740 frames in 5.1 seconds = 1121.215 FPS
11318 frames in 5.0 seconds = 2255.385 FPS
11695 frames in 5.0 seconds = 2329.950 FPS
11544 frames in 5.0 seconds = 2287.631 FPS
11210 frames in 5.0 seconds = 2231.899 FPS
11184 frames in 5.0 seconds = 2215.631 FPS
12403 frames in 5.0 seconds = 2472.036 FPS
11780 frames in 5.0 seconds = 2348.274 FPS
11367 frames in 5.0 seconds = 2263.728 FPS
11360 frames in 5.0 seconds = 2270.291 FPS


```

---

### Post by arsenic23 on 2007-07-12
> then after that you need to install beryl using aiglx (and nog XGL) i don't really know the difference but i know that for intel cards aiglx is MUCH better and faster

You shouldn't have to install either in Feisty.  It should work without them.

---

### Post by duydaniel on 2007-07-12
how do I know if my graphic driver is okey?
I follow the compiz guide... and stuck at the place where it read:

> Add the key
```
Code:

gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add -

```


I have no idea what "add key" meant :confused:

---

### Post by AndrewGene on 2007-07-12
Don't give up, it's not so bad. It is good that you can't find beryl anymore.  You don't need it.
Did you install emerald?

---

### Post by AndrewGene on 2007-07-12
The key is like a password to enter the repository.  Simply copy and paste that code.  It just allows you to actually use what is in the repository.

---

### Post by walkerk on 2007-07-12
> **kavon89 said:**
> I don't know why you expect the cool Beryl effects with your integrated Intel graphics display. It's not happening, especially for integrated display unless you want your desktop to become a sideshow.  Come back with an Nvidia card or a good ATI card and try Beryl.

I have onboard Intel 945GM video running Compiz Fusion with all the effects.. smoothly.. you don't need an nvidia or ati card for this.. perhaps he'd think to "upgrade" if he plays games.. otherwise it will suffice..

Beryl as well..

---

### Post by duydaniel on 2007-07-12
> **AndrewGene said:**
> Don't give up, it's not so bad. It is good that you can't find beryl anymore.  You don't need it.
Did you install emerald?

I have installed emerald in synaptic.

In the stage:
> Quote:
Add the key
Code:

Code:

gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add -

I have no idea what "add key" meant 

I typed the first line of "add key" in the terminal:
```
daniel@daniel-laptop:~$ gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg: requesting key 81836EBF from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
daniel@daniel-laptop:~$ 

```

any idea? My internet connection is working fine

---

### Post by walkerk on 2007-07-12
> **duydaniel said:**
> I have installed emerald in synaptic.

In the stage:


I typed the first line of "add key" in the terminal:
```
daniel@daniel-laptop:~$ gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg: requesting key 81836EBF from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error
daniel@daniel-laptop:~$ 

```

any idea? My internet connection is working fine

If you're having this much trouble with beryl give up and install [Compiz Fusion using Vorian's guide]("http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion"). ** It works well with Intel 945GM onboard video.. I have a 6400 w/ this video.** Before you install Compiz Fusion remove everything that has to do with Compiz and Beryl through Synaptic. After which install emerald via Synaptic and reboot.

To load Compiz Fusion w/ Emerald:
```
compiz --replace -c emerald
```

Let us know..

---

### Post by AndrewGene on 2007-07-12
I believe he is following vorian's guide.  You need to paste these two lines TOGETHER in the terminal...

gpg --keyserver subkeys.pgp.net --recv-keys 81836EBF
gpg --export --armor 81836EBF | sudo apt-key add -

...before you press enter for the first time

---

### Post by duydaniel on 2007-07-12
problem!!!

I thought it was like windows (automatically detect and reinstall graphic driver)... so I tried to "uninstall" in synaptic Intel drivers... then reboot the system.
Now... it reported something about windows X... and led me to a dark screen (terminal).

I still have Vista on my Laptop so I go to Vista and replied you people. Sound like big trouble.

---

### Post by walkerk on 2007-07-12
> **duydaniel said:**
> problem!!!

I thought it was like windows (automatically detect and reinstall graphic driver)... so I tried to "uninstall" in synaptic Intel drivers... then reboot the system.
Now... it reported something about windows X... and led me to a dark windows (terminal).

I still have Vista on my Laptop so I go to Vista and replied you people. Sound like big trouble.

```
sudo apt-get install xserver-xorg-video-intel
```

?

---

### Post by sneax on 2007-07-12
> **duydaniel said:**
> I should give up on that things...
since windows DOS -> 3.11 -> Vista... I never have such tough time.:(

maybe they don't like me saying this here but maybe try some other distributions? i was very happy with pclinuxos, opensuse and mepis - they are all very easy to install and changes are that using one of those beryl will work out of the box or there will be a very easy howto

---

### Post by duydaniel on 2007-07-12
> **walkerk said:**
> ```
sudo apt-get install xserver-xorg-video-intel
```

?

it can't download the file since it can't connect to the internet both wired and wireless. If there is someone does not give up... then neither do I.

---

### Post by duydaniel on 2007-07-12
> **sneax said:**
> maybe they don't like me saying this here but maybe try some other distributions? i was very happy with pclinuxos, opensuse and mepis - they are all very easy to install and changes are that using one of those beryl will work out of the box or there will be a very easy howto

I think we are all in Linux ... I think the ppl here would glad to help you too even if you are using different distro. They probably don't get pay to help me... and are willingly to take challenge. So do I.

---

### Post by tgm4883 on 2007-07-12
> **duydaniel said:**
> it can't download the file since it can't connect to the internet both wired and wireless.

from command line

sudo ifconfig eth0 up
sudo dhclient

---

### Post by duydaniel on 2007-07-12
> **tgm4883 said:**
> from command line

sudo ifconfig eth0 up
sudo dhclient

:guitar: I am back on Ubuntu now... :) it works like charm sir... Thanks :KS
Let me read some previous post to install the Compiz...

---

### Post by duydaniel on 2007-07-12
> **walkerk said:**
> If you're having this much trouble with beryl give up and install [Compiz Fusion using Vorian's guide]("http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion"). ** It works well with Intel 945GM onboard video.. I have a 6400 w/ this video.** Before you install Compiz Fusion remove everything that has to do with Compiz and Beryl through Synaptic. After which install emerald via Synaptic and reboot.

To load Compiz Fusion w/ Emerald:
```
compiz --replace -c emerald
```

Let us know..

my system is clean now... would you please tell me which step to do first, second... third?
do the guide first? or install "emerald vie synaptic' first or  > To load Compiz Fusion w/ Emerald:
```
compiz --replace -c emerald
```

Is there anyway to check if the onboard driver work correctly? My system runs normally, but just in case... something wrong could happen :KS

---

### Post by duydaniel on 2007-07-12
I have done all the steps in the compiz guide...
when I run:
```

compiz --replace -c emerald
```

by Alt + F2 it did not work... (with selected 'Run in terminal' => a blank windows poped up and gone... real quick. --------  without selected 'run in terminal' => nothing happened.)

the same with:

```
compiz --replace

```

I also found out that Beryl is installed in my system after finish the compiz guide :confused:

---

### Post by duydaniel on 2007-07-13
in the final step to run Compiz

```

daniel@daniel-laptop:~/Desktop/compiz-0.4.0$ compiz --replace -c emerald &
[1] 11440
daniel@daniel-laptop:~/Desktop/compiz-0.4.0$ Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

[1]+  Exit 1                  compiz --replace -c emerald
daniel@daniel-laptop:~/Desktop/compiz-0.4.0$ 

```

That error occurred. :confused: Intel 945GM

---

### Post by vapore0n on 2007-07-13
Too many confusing posts for the OP. Maybe that's why he still cant get it to work?

I got an intel 945g and here is what I did:

reformat
re-install ubuntu feisty

follow these instructions: [https://help.ubuntu.com/community/BerylOnFeisty](https://help.ubuntu.com/community/BerylOnFeisty)

the default drivers work with beryl. Only problem is that Feisty broke something in the drivers and now Blur doesnt work properly. It is supposedly fixed for the next release though.

---

### Post by duydaniel on 2007-07-13
> **vapore0n said:**
> Too many confusing posts for the OP. Maybe that's why he still cant get it to work?

I got an intel 945g and here is what I did:

reformat
re-install ubuntu feisty

follow these instructions: [https://help.ubuntu.com/community/BerylOnFeisty](https://help.ubuntu.com/community/BerylOnFeisty)

the default drivers work with beryl. Only problem is that Feisty broke something in the drivers and now Blur doesnt work properly. It is supposedly fixed for the next release though.

I had gone thru many freaking days... trying to install the Dell Wireless card. Now, if I "format"... then I would have to start everything from scratch... I also have the Ubuntu Ultimate 1.4 which is feisty Should I, if I decide to reformat, install the Ultimate version instead of the official??? :confused:

---

### Post by tgm4883 on 2007-07-13
> **vapore0n said:**
> Too many confusing posts for the OP. Maybe that's why he still cant get it to work?

I got an intel 945g and here is what I did:

reformat
re-install ubuntu feisty

follow these instructions: [https://help.ubuntu.com/community/BerylOnFeisty](https://help.ubuntu.com/community/BerylOnFeisty)

the default drivers work with beryl. Only problem is that Feisty broke something in the drivers and now Blur doesnt work properly. It is supposedly fixed for the next release though.

If your going to tell the OP to reinstall, WHY on earth would you tell him to install discontinued software and not Compiz Fusion?

---

### Post by duydaniel on 2007-07-13
Since I'm gonna reinstall Ubuntu... do you advise me to go with 64 bit version?

---

### Post by PriceChild on 2007-07-13
I haven't a clue why this thread lasted so long... that card will let you run compiz out of the box from system > preferences > desktop effects.

I would stick to 32bit for best compatability and range of applications.

---

### Post by tgm4883 on 2007-07-13
> **PriceChild said:**
> I haven't a clue why this thread lasted so long... that card will let you run compiz out of the box from system > preferences > desktop effects.

I would stick to 32bit for best compatability and range of applications.

Because the OP doesn't want to run desktop effects.  They want to run beryl (or compiz fusion)

And I would run the 64-bit.  And I will even give you something to help you make your decision, rather than interject my own false beliefs.  Don't make me sick kliz on you ;)

A sticky in the 64-bit forum.
[Pease Read First Advantages and Disadvantages of 64bit. (Plus install Guides)]("http://ubuntuforums.org/showthread.php?t=368607")

---

### Post by duydaniel on 2007-07-13
> **PriceChild said:**
> I haven't a clue why this thread lasted so long... that card will let you run compiz out of the box from system > preferences > desktop effects.

I would stick to 32bit for best compatability and range of applications.

You know what the problem was?
The desktop effects worked in the beginning... but the resolution wasn't right. Then... I googled for many solutions... finally, the system messed up because too many... different confused solutions.
I got the acceptable resolution... but the desktop effects then messed up...

All freaking days.

I would glad if tgm4883 responded a little bit early since I already reinstall Mr Ubuntu 32 bit. Since I like to play around with the system... as I did with Windows Me (I used to reinstalled it at least 20 times due to damages..., of course, due to too many times reinstall I memorized the serial key)..., the system probably won't survive long. Next time I will try Ubuntu 64 bit. :popcorn:

Now... I am updating the system... is it safe that I will go with the Compiz guide?

---

### Post by tgm4883 on 2007-07-13
yea, install the 915resolution package and then do the mini how to for compiz fusion.  It worked for me so it should work for you.

---

### Post by duydaniel on 2007-07-13
> **tgm4883 said:**
> yea, install the 915resolution package and then do the mini how to for compiz fusion.  It worked for me so it should work for you.

Hey, do you have the guide for 915resolution and the guide for compiz... I don't want to get a wrong guide which after some sudo... blah blah blah... bring me catastrophe. :(

---

### Post by tgm4883 on 2007-07-13
> **duydaniel said:**
> Hey, do you have the guide for 915resolution and the guide for compiz... I don't want to get a wrong guide which after some sudo... blah blah blah... bring me catastrophe. :(

915 resolution 
sudo apt-get install 915resolution
then do ctrl-alt-backspace

Compiz fusion guide
[http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion)

---

### Post by duydaniel on 2007-07-14
> **tgm4883 said:**
> 915 resolution 
sudo apt-get install 915resolution
then do ctrl-alt-backspace

Compiz fusion guide
[http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion](http://ubuntuforums.org/showthread.php?t=481314&highlight=compiz+fusion)

:lolflag: Work like charm sir!!! :guitar:
But the wireless now get problem :(
[http://ubuntuforums.org/showthread.php?t=500490](http://ubuntuforums.org/showthread.php?t=500490)

I deeply appreciate your "Ubuntu"-- Human being to other!!! Let me joint!!! :KS

---

### Post by tomaasj on 2007-07-14
> **duydaniel said:**
> I am sorry. But I have used windows since 3.11 -> Vista and finally been convinced that Windows sucks.

I switch to Linux... my Laptop is Dell 6400 with Intel 945GM graphic card.

I did my best on trying google to make it work with Beryl... but it can't. There are many posts show how to do it... but I still not be able to do it. Probably, they are complicated and assumed pre-knowledge about Linux. I was so painful to look for drivers to me. It took me days to make the Dell wireless work, but I stuck with the graphic card now.

I am new to Linux and only know how to copy and paste commands into terminal.
I would appreciate if you have something "easy to understand" guide to install the Intel945GM correctly... making it works with Beryl.

I have the same laptop and Beryl worked until I increased the resolution to 1280 800.  See my posting:

[http://ubuntuforums.org/showthread.php?t=500574&highlight=tomaasj](http://ubuntuforums.org/showthread.php?t=500574&highlight=tomaasj)

I am not able to solve the problem.  I also would appreciate help on this.

gr. Tomaasj

---

