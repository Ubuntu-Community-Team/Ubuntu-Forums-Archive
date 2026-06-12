---
title: "Logon Screen Resolution"
date: 2009-05-23
forum: General Help
---

### Post by jshurst on 2009-05-23
I've read about this before but can't seem to solve my problem.  I've installed Ubuntu and it works fine on a CRT monitor.  However, I want to connect it to a 50 inch Samsung plasma TV.  When I boot it up it says "Mode not supported."  If I boot it and then log in with the CRT then remove then change it to the plasma it works fine.  I have Gnome set to run at 1024x768, which is probably pretty low, but does show up and look good on the plasma.

Can someone tell me how to change the logon screen to be 1024x768.  I read that you can change it on the xorg.conf file but I don't see any place for that.  Here is what I have in my file:

```


Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

Thanks in advance,

J

---

### Post by BslBryan on 2009-05-23
Hello, jshurst. :-)

I recently helped someone out with this on Launchpad, and the way we solved it was to change the xorg.conf to look like this: (make sure you back it up first!)
```
Section "Monitor"
 Identifier "Configured Monitor"
 Vendorname "Generic LCD Display"
 Modelname "LCD Panel 1280x1024"
 Horizsync 31.5-64.0
 Vertrefresh 56.0 - 65.0
  modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync
+vsync
  modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806
-vsync -hsync
  Gamma 1.0
EndSection

Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
 Defaultdepth 24
 SubSection "Display"
  Depth 24
  Virtual 1024 768

Modes "800x600@60" "1024x768@60" 
 EndSubSection
EndSection
```

Know that I am modifying the code from even its original solution.  His screen resolution was 1280x1024.  Also, the solution worked, but the bootsplash became very large, so I left 800x600 in the code.

I really hope this works for you!

Best to you, and good luck! :-)

---

### Post by Legace on 2009-05-23
Open Terminal.
Type in:
```
sudo gedit /etc/X11/xorg.conf
```

then replace your current "Screen" section with the one below:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Modes      "1024x768"
	EndSubSection
EndSection
```

Finally, save, and reboot.

---

