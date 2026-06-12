---
title: "How enable engadget or those mac like  menu in Gnome"
date: 2009-07-17
forum: Desktop Environments
---

### Post by ramnarayan on 2009-07-17
Hi

am running 9.04 on a t60 with 4 GB RAM and an ATI X1300 graphics card.

Compiz does not work ?? and even though the packages are installed it does not appear as a menu item anywhere

But my real question is i want to enable a menu panel - like in KDE or MAC (I think ) the one that floats around at the bottom and on hovering above a icon it bloats up proudly.

i have installed gdesklets but that too does not seem to do the job.

---

### Post by ~sHyLoCk~ on 2009-07-17
> **ramnarayan said:**
> Hi

am running 9.04 on a t60 with 4 GB RAM and an ATI X1300 graphics card.

Compiz does not work ?? and even though the packages are installed it does not appear as a menu item anywhere

But my real question is i want to enable a menu panel - like in KDE or MAC (I think ) the one that floats around at the bottom and on hovering above a icon it bloats up proudly.

i have installed gdesklets but that too does not seem to do the job.

Install cairo-dock and cairo-dock-plugins. Btw why shouldn't compiz work? Did you install ccsm? Also install fusion-icon.

---

### Post by ramnarayan on 2009-07-17
> **~sHyLoCk~ said:**
>  Btw why shouldn't compiz work? Did you install ccsm? Also install fusion-icon.

It does'nt - no idea why ??

---

### Post by ~sHyLoCk~ on 2009-07-17
> **ramnarayan said:**
> It does'nt - no idea why ??

Try and see what happens
```
compiz --replace&
```

---

### Post by ramnarayan on 2009-07-17
> **~sHyLoCk~ said:**
> Try and see what happens
```
compiz --replace&
```

something worked - Ok something worked

so now how do i get that compiz user menu to control stuff ??

thanks

---

### Post by ~sHyLoCk~ on 2009-07-17
> **ramnarayan said:**
> something worked - Ok something worked

so now how do i get that compiz user menu to control stuff ??

thanks

```
ccsm&
```

If it doesn't appear that means you don't have it installed. Do:
```
sudo apt-get install ccsm
```

---

### Post by ramnarayan on 2009-07-17
Not sure what i did

along with attempting to do compiz i also was installing an ati driver package flgrx??something and now i have got locked out of my 9.04 - very stupid

tried recovery and clean and repair broken packages and even booting from an older kernal 

all i get is a stupid messed up screen 

am not sure what the package was called - sure it was something like flgrx-ccd or something ??

so stuck without 9.04

But hey no sweat booted into 7.10 (my back up default ubuntu) and will figure something out :-)

---

### Post by features on 2009-07-17
The fglrx driver in Jaunty will not work nicely with your X1300 - it doesn't with mine.  This is because ATI have relegated support for these cards to the open source drivers from Catalyst 9.04 onwards.  You could try the Catalyst 9.03 driver which is the latest to support your card, but I don't think that supports the version of Xorg that ships with 9.04.

Rock, meet hard place.

The best suggestion is to install the ati drivers from the ubuntu repos or to install them from the xorg edgers ppa.

You will need to uninstall the fglrx drivers first though.

HTH

---

### Post by ramnarayan on 2009-07-17
> **features said:**
> 
Rock, meet hard place.

met and now its in trouble both the rock and the hard place ;-)



> **features said:**
> 
You will need to uninstall the fglrx drivers first though.

HTH

This is is the question, what package and how

---

### Post by Deiutzu on 2009-07-17
Hello

I had a similar problem on an ATI Radeon Xpress. First, start Ubuntu in terminal from the boot menu (press esc when asked or follow the instructions described here [http://ubuntuforums.org/showthread.php?t=362597](http://ubuntuforums.org/showthread.php?t=362597) Then, remove the faulty driver by using the command```
 sudo apt-get remove fglrx
```. Also remove x org drivers by using ```
sudo apt-get remove xserver-xorg
```, then reinstall them with the command ```
sudo apt-get install xserver-xorg
```. Then reboot. You will now have the original driver but no hardware acceleration. You ca try out different drivers from here.

Hope this helps!

Best regards, 

Andrei C.

---

### Post by features on 2009-07-17
> **Deiutzu said:**
> Hello

I had a similar problem on an ATI Radeon Xpress. First, start Ubuntu in terminal from the boot menu (press esc when asked or follow the instructions described here [http://ubuntuforums.org/showthread.php?t=362597](http://ubuntuforums.org/showthread.php?t=362597) Then, remove the faulty driver by using the command```
 sudo apt-get remove fglrx
```. Also remove x org drivers by using ```
sudo apt-get remove xserver-xorg
```, then reinstall them with the command ```
sudo apt-get install xserver-xorg
```. Then reboot. You will now have the original driver but no hardware acceleration. You ca try out different drivers from here.


Yes, do this (thanks Andrei, much better than what I was going to suggest)

I'll include my xorg.conf which is a working setup for the ati drivers.  Note you may get some screen flickering with the ones in Jaunty's repos.  It also doesn't play nice with Emerald, if you want to use that.  But it will get you compiz, at least.  I hope it's useful


**If you use dual monitors, then you will need to set your virtual resolution in the SCREEN section**

```


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

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
EndSection


Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"

	Identifier  "aticonfig-Device[0]-0"
	Driver      "ati"
	BusID       "PCI:1:0:0"
	Option      "AccelMethod" "EXA" # Valid options are XAA and EXA, XAA old, reliable & default, EXA newer faster
	Option "EnablePageFlip" "TRUE" # page flipping for 3D accel, increases performance but doesn't work in rare cases, hence default is off.
	Option "FBTexPercent" "50" # with EXA 0 may be faster but may cause probs, XAA no real efect, default 50
	Option "DMAForXv" "TRUE" # Default on speed up playing video
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
#		Virtual 2560 1024  Set your own resolution here if you use dual head
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

Section "DRI"
Group        "video"
 Mode         0666
EndSection


```

---

### Post by ramnarayan on 2009-07-17
I solved the problem by installing Linux Mint 7 (also an excuse to try it out)

however will revert to 9.04 in a while after attending to some jobs.

So while i have not used the solutions suggested am marking it as solved. Since it does tell me how

Thanks folks

---

### Post by ramnarayan on 2009-07-20
Bump

Ok 
I am back on a stable 9.04 (i think stable)

so would despertely like to have some eye candy

Like those menu's in KDE and MAC where the menu icons spring up when you hover over them

Any ideas ??

---

### Post by fabounet on 2009-07-20
here you go :)
[http://www.cairo-dock.org/ww_page.php?p=By%20distributions&lang=en]("http://www.cairo-dock.org/ww_page.php?p=By%20distributions&lang=en")

---

### Post by ramnarayan on 2009-07-20
Cairo works

marking this solved 

thanks folks / ubuntu friends :-)

---

