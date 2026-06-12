---
title: "Ooops... I've just nuked xorg"
date: 2009-06-07
forum: General Help
---

### Post by Powderhound01 on 2009-06-07
OK, in the process of trying to get my MX518 working today, I accidentally screwed up my xorg.conf, and then realised that I didn't have a backup. I've tried reconfiguring it in recovery mode root prompt, but even then I still don't get past the Ubuntu loading screen. What else can I do bar a full reinstall?

---

### Post by utnubuuser on 2009-06-07
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Powderhound01 on 2009-06-07
Done, to no effect.

---

### Post by jbruced on 2009-06-07
Tried renaming it, then using recovery to recreate a new one?

---

### Post by Powderhound01 on 2009-06-07
How would I go about doing that. I've got an exam tomorrow, so I can't face any bash tonight, so could people post any other suggestions and I can try them all in one go tomorrow evening.

Also, I tried to recover from a live disk, but I'm getting a Buffer I/O in FD0 error when I try to load. There was something that I had to append to the F6 menu, but I can't remember what it was for the life of me- any help here? I assume being in the live environment would make things a bit simpler to fix.

---

### Post by Yellow Pasque on 2009-06-07
Can you post the /var/log/Xorg.0.log from the filesystem in question (i.e. not the LiveCD's Xorg log)

---

### Post by Powderhound01 on 2009-06-07
Again, how do I access that? I'm not very confident in bash.

---

### Post by jbruced on 2009-06-07
> **jbruced said:**
> Tried renaming it, then using recovery to recreate a new one?

go to terminal

sudo mv /etc/X11/xorg.conf /etc/X11/whateveryouwanttocallit
exit 


now reboot and recreate xorg.conf from recovery

---

### Post by Powderhound01 on 2009-06-08
No joy. If it helps, I get a repeating scrambled pattern (Possibly a distortion of the splash screen?) all the way across the top couple of hundred pixels on my monitor, which appears for two seconds, disappears, then returns and freezes.

---

### Post by utnubuuser on 2009-06-09
You probably have to use the liveCD with noapic or nolapic or whatever.  at the first screen use F6 then select noapic etc.

to get at a terminal and redo a xorg.conf file,  in grub use the arrow keys to select the entry that says "recovery mode", then select "drop to shell", or even the xfix option to fix the xserver.

kinda sounds like the machine is using the fglrx driver for ati, and that's kinda buggy.  

you might be able to check if that's the case by running jockey-gtk from your recovery console, then disabling or enabling the proprietary driver.

When you run > sudo dpkg-reconfigure -phigh xserver-xorg from a terminal or recovery console, it creates a new xorg.conf file and stores the old one as a backup as xorg.conf20090607whateverdateandtimeis.

those squiggly lines means it's most likely the driver, - > sudo jockey-gtk - if a driver's enabled, disable it, then restart. If there's one listed, but disabled, try enabling, then restarting.

PS have you checked in /etc/X11 to see if an automatic backup was  created before you made the original changes?  Gedit makes backups by default.

---

### Post by Powderhound01 on 2009-06-13
> **utnubuuser said:**
> You probably have to use the liveCD with noapic or nolapic or whatever.  at the first screen use F6 then select noapic etc.

to get at a terminal and redo a xorg.conf file,  in grub use the arrow keys to select the entry that says "recovery mode", then select "drop to shell", or even the xfix option to fix the xserver.

kinda sounds like the machine is using the fglrx driver for ati, and that's kinda buggy.  

you might be able to check if that's the case by running jockey-gtk from your recovery console, then disabling or enabling the proprietary driver.

When you run  from a terminal or recovery console, it creates a new xorg.conf file and stores the old one as a backup as xorg.conf20090607whateverdateandtimeis.

those squiggly lines means it's most likely the driver, -  - if a driver's enabled, disable it, then restart. If there's one listed, but disabled, try enabling, then restarting.

PS have you checked in /etc/X11 to see if an automatic backup was  created before you made the original changes?  Gedit makes backups by default.

Thanks for your help. What I was originally trying to achieve was to get the side buttons working on my mouse again. I'm guessing the issue is that 9.04 switches to the HAL for mouse instead of xorg. How do I go about getting them working again? I only need it in Firefox, if that simplifies things.

---

### Post by gradinaruvasile on 2009-06-13
Try editing xorg.conf from recovery console (select root prompt)
After executing

dpkg-reconfigure -phigh xserver-xorg

type

nano /etc/x11/xorg.conf
scroll down to 

Section "Device"
        Identifier "whateverisyours"
        [COLOR="Red"]Driver "vesa"[/COLOR]

And insert the driver line (red one).
ctrl-o
enter
ctrl-x
ctrl-d

The recovery menu appears again

Select "Resume booting" (the upper line)

This will set the driver to your card to the fallback driver (vesa). 
Then you should remove the fglrx drivers completely from synaptic 
Search for fglrx
(select every installed package with fglrx in its namemark for complete removal)

Reboot

---

### Post by Powderhound01 on 2009-06-13
> **gradinaruvasile said:**
> Try editing xorg.conf from recovery console (select root prompt)
After executing

dpkg-reconfigure -phigh xserver-xorg

type

nano /etc/x11/xorg.conf
scroll down to 

Section "Device"
        Identifier "whateverisyours"
        [COLOR="Red"]Driver "vesa"[/COLOR]

And insert the driver line (red one).
ctrl-o
enter
ctrl-x
ctrl-d

The recovery menu appears again

Select "Resume booting" (the upper line)

This will set the driver to your card to the fallback driver (vesa). 
Then you should remove the fglrx drivers completely from synaptic 
Search for fglrx
(select every installed package with fglrx in its namemark for complete removal)

Reboot

Sorry if I was ambiguous; I've fixed it now. I'm trying to get the mouse to work now.

---

### Post by PmDematagoda on 2009-06-13
> **Powderhound01 said:**
> Sorry if I was ambiguous; I've fixed it now. I'm trying to get the mouse to work now.

Could you please post the contents of /etc/X11/xorg.conf? If you are unable to, then just get rid of everything with/under the word "InputDevice" in the configuration file, this probably may be what's causing the problem.

---

### Post by Powderhound01 on 2009-06-13
> **PmDematagoda said:**
> Could you please post the contents of /etc/X11/xorg.conf? If you are unable to, then just get rid of everything with/under the word "InputDevice" in the configuration file, this probably may be what's causing the problem.

I've already commented them out (#) with no effect.

---

### Post by PmDematagoda on 2009-06-13
> **Powderhound01 said:**
> I've already commented them out (#) with no effect.

Well, apart from posting the contents of xorg.conf(which would really be useful), there is one more thing you can try. Try moving your xorg.conf to a different location such that there is no xorg.conf and then try starting X again, since your hardware has an open source alternative, it should start up properly and the input devices should be detected, so then you could try posting the contents of xorg.conf.

A suggestion to moving the xorg.conf file:-
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.orig.bak
```

---

### Post by Powderhound01 on 2009-06-14
> # xorg.conf (X.Org X Window System server configuration file)
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
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"gb"
#EndSection
# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

#Section "InputDevice"
#      Identifier      "Configured Mouse"
#       Driver          "evdev"
#       Option          "CorePointer"
#       Option          "Buttons"       "7"
#       Option          "ZAxisMapping"  "4 5"
#       Option          "ButtonMapping" "1 2 3 6 7"
#       Option          "Name"  "Logitech USB-PS/2 Optical Mouse"
#EndSection

There you go.

---

