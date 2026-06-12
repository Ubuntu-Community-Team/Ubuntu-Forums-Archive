---
title: "white screen of death"
date: 2009-06-05
forum: General Help
---

### Post by gogreenpower on 2009-06-05
i was trying to resolve a few issues i had, nothing to serious but one of my fixes was to remove my video driver, reboot and reinstall, but now once i login i've got the white screen of death. i've tried xfix, reconfigure xserver, startx tells me nothing, and now im at a loss. im using 9.04 with an ATI graphics chip. i removed it via the system/administration/hardware drivers gui.

Help!

---

### Post by gogreenpower on 2009-06-05
bump

---

### Post by Legace on 2009-06-05
You installed the FGLRX driver, right?

If so, follow these steps:
> **gocek said:**
> 
Reboot PC, select "Recovery mode" in boot-manager (GRUB) and then go for "root shell" option (you might need to press the DOWN arrow a couple of times). 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```

then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.


And this is how to install the drivers properly:
[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_restricted_drivers_manually)

and do the "manual installation" STEP BY STEP.

---

### Post by gogreenpower on 2009-06-05
when i type, 

*sudo dpkg-reconfigure xserver-xorg*

i get, 

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20090606104315

and its still the same when i log in after reboot.

is it possible to reinstall the drivers through the root shell?

---

### Post by Legace on 2009-06-06
Type the following in root shell:
```
sudo nano /etc/X11/xorg.conf
```

and edit the file so it looks like:
```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

---

### Post by gogreenpower on 2009-06-06
done, it was the same as that but in a different order, still have the WSOD.

---

### Post by gogreenpower on 2009-06-06
when i type startx i get

fatal server error:
server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again


???? 

i removed the /tmp/.X0-lock and now i get

_XSERVTransSocketUNIXCeateListener: ...SocketCreateListener() failed
_XSERVTransMakeALLCOTSServerListereners: server already running

fatal server error:
cannot establish any listening sockets - make sure an X server isnt already running


????

---

