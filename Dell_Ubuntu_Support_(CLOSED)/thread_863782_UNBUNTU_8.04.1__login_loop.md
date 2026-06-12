---
title: "UNBUNTU 8.04.1  login loop"
date: 2008-07-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gcapwell on 2008-07-18
I,ve loaded UBUNTU 8.04.1 on my pc with sucess, however when I login correctly I keep getting looped logins. Keeps asking me to login again.
Thanks for your help
Gary

---

### Post by falcon61102 on 2008-07-18
This may be due to the graphics setup or drivers that you have.  Have you tried booting up the Failsafe version, normally the second option in the GRUB?  Try that and see if that works.  Also, then you can install the correct video drivers or adjust your screen as needed.

---

### Post by symon1980 on 2008-07-19
gcapwell, Do you by any chance have an ATI Radeon Xpress series Graphics Card???
symon.

---

### Post by gcapwell on 2008-07-19
Thanks , I'll try failsafe as soon as possible, the pc in question is in work. My pc at home works great.
Gary

---

### Post by gcapwell on 2008-07-19
Thank you, I'm not sure about the graphics card. As soon as I get to work I'll check and get back to you.
Gary

---

### Post by gcapwell on 2008-07-19
> **falcon61102 said:**
> This may be due to the graphics setup or drivers that you have.  Have you tried booting up the Failsafe version, normally the second option in the GRUB?  Try that and see if that works.  Also, then you can install the correct video drivers or adjust your screen as needed.


:)Thanks , I'll try failsafe as soon as possible, the pc in question is in work. My pc at home works great.
Gary

---

### Post by gcapwell on 2008-07-19
> **symon1980 said:**
> gcapwell, Do you by any chance have an ATI Radeon Xpress series Graphics Card???
symon.

:)Thank you, I'm not sure about the graphics card. As soon as I get to work I'll check and get back to you.
Gary

---

### Post by symon1980 on 2008-07-19
im willing to bet it is ;)
i have the same problem with my older computer, its a bug in 
hardy that conflicts with Radeon xpress series graphics cards...
i believe the work around was to remove compiz. heres the bug page.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/188660](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/188660)

I personally couldn't get the workaround to work... so i just installed pclinuxos on my older computer

---

### Post by gcapwell on 2008-07-21
> **falcon61102 said:**
> This may be due to the graphics setup or drivers that you have.  Have you tried booting up the Failsafe version, normally the second option in the GRUB?  Try that and see if that works.  Also, then you can install the correct video drivers or adjust your screen as needed.


:( Yes, I booted to failsafe. This allowed me to ENABLE the ATI Radeon driver. Upon reboot I have a message " frequency out of sync" on the screen and nothing more happens.

---

### Post by gcapwell on 2008-07-21
> **symon1980 said:**
> gcapwell, Do you by any chance have an ATI Radeon Xpress series Graphics Card???
symon.

Your right on.........my graphics card is a ATI RADEON XPRESS 200 series.

---

### Post by saidinesh5 on 2008-07-21
yea i had that problem too..it was due to the graphics card..it vanished when i booted through the fail safe mode and installed the prop. drive for the graphics card..i have the same graphics card...
all the best

---

### Post by falcon61102 on 2008-07-21
If that bug work around doesn't work that symon1980 posted, you could try editing your xorg.conf manually because that sounds like your refresh rate is wrong.

---

### Post by gcapwell on 2008-07-22
> **falcon61102 said:**
> If that bug work around doesn't work that symon1980 posted, you could try editing your xorg.conf manually because that sounds like your refresh rate is wrong.

I logged in on failsafe and installed the graphics driver they recommended, rebooted, got a screen " out of frequency, h:75.0 khz / v:60.0 hz. OPPS.........now I'm stumped.
Gary

---

### Post by falcon61102 on 2008-07-22
It looks like you monitor is trying to use two different refresh rates for the screen at the same time.  Boot back up in failsafe and run:
```
sudo gedit /etc/X11/xorg.conf
```

Post that here and I'll help you find what you have to edit, unless your graphics drivers came with a config utility, then you can use that.  Either way, post it up here though.

---

### Post by gcapwell on 2008-07-25
> **falcon61102 said:**
> It looks like you monitor is trying to use two different refresh rates for the screen at the same time.  Boot back up in failsafe and run:
```
sudo gedit /etc/X11/xorg.conf
```

Post that here and I'll help you find what you have to edit, unless your graphics drivers came with a config utility, then you can use that.  Either way, post it up here though.


How do I run the CODE in ubuntu? I'm still new at this OS.
Thanks
Gary

---

### Post by falcon61102 on 2008-07-25
Go to Applications>Accessories>Terminal in the menus that should be in the upper right hand corner of your screen.  The terminal is like the command prompt from windows, just more powerful.

---

### Post by gcapwell on 2008-07-28
> **falcon61102 said:**
> Go to Applications>Accessories>Terminal in the menus that should be in the upper right hand corner of your screen.  The terminal is like the command prompt from windows, just more powerful.

First of all.........thanks for your help in this matter. OK, I've been there and can not find any file  named " sudo gedit /etc/X11/xorg.conf "
The files go up to " sudo gedit /etc " but the extention " X11/xorg.conf "
do not exsist.
GARY

---

### Post by falcon61102 on 2008-07-28
What happens if you copy and paste that line of code into your terminal?

To paste, you need to right click and select paste, CTRL-V won't work in the terminal.

---

### Post by gcapwell on 2008-07-28
> **falcon61102 said:**
> What happens if you copy and paste that line of code into your terminal?

To paste, you need to right click and select paste, CTRL-V won't work in the terminal.

That worked..........here it is

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
EndSection

---

### Post by falcon61102 on 2008-07-28
Try this: go to your terminal and type in:
```
sudo displayconfig-gtk
```

That should load a GUI window that will allow you to adjust your graphics settings.  See if you can adjust them to your desired settings.  

If not, try to reinstall you drivers.  If it makes it easier, you can use Envy.  Go to your terminal and type:
```
sudo apt-get install envyng-gtk
```

That should install it, if you get an error about an unknown application, just try "envy" instead of "envyng."  I don't have Ubuntu loaded right now... going off memory.  Another way you can install Envy is through the Synaptic Package Manager; start that and run a search for Envy, it should come right up.  Envy will allow you to install and uninstally drivers for you card quite easily.

---

### Post by gcapwell on 2008-07-30
> **falcon61102 said:**
> Try this: go to your terminal and type in:
```
sudo displayconfig-gtk
```

That should load a GUI window that will allow you to adjust your graphics settings.  See if you can adjust them to your desired settings.  

If not, try to reinstall you drivers.  If it makes it easier, you can use Envy.  Go to your terminal and type:
```
sudo apt-get install envyng-gtk
```

That should install it, if you get an error about an unknown application, just try "envy" instead of "envyng."  I don't have Ubuntu loaded right now... going off memory.  Another way you can install Envy is through the Synaptic Package Manager; start that and run a search for Envy, it should come right up.  Envy will allow you to install and uninstally drivers for you card quite easily.

:KS Well, I guess I've done about all I can trying to clean up the graphics on this PC. I do have a somewhat decent 2D screen, be it pulled in around the sides a little. Some times things don't always go the way we'd like. Anyway, I'll be getting a new graphics card and that will solve the glitch.
Thanks again for all your help and patience in this matter. Have a GREAT day! :)
Gary

---

