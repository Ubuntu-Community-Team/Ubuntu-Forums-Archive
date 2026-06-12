---
title: "cannot save display setting"
date: 2009-04-25
forum: Desktop Environments
---

### Post by azurehi on 2009-04-25
After installing xubuntu 9.04, using settings manager from applications, I choose 1152 x 864, apply.  After restart, the setting is Not saved.

How are settings saved in xubuntu/xfce?  Thanks.

---

### Post by Saint_ on 2009-04-26
If you're using KDE, you might try upgrading to 4.2 (i had the same problem, only with saving the background, etc). If that's not the case, then I guess I'm not much use lol, but I figured I'd through my 2 cents worth.

---

### Post by molibden on 2009-04-26
I experience the same problem as azurehi. I installed Xubuntu 9.04 on a pc with a crt display and after restart the system ignores resolution and refresh rate settings and switches to highest possible resolution (i.e. 1280x960).

It seems that the problem concerns other versions of ubuntu as well, not only xubuntu: [http://ubuntuforums.org/showthread.php?t=1122558]("http://ubuntuforums.org/showthread.php?t=1122558").

I haven't tried to use the script from the above thread, so I don't know if it works. I'll try it tomorrow.

**Edit:** I solved the problem by editing /etc/X11/xorg.conf:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection
```

---

### Post by abdusamed on 2009-10-14
hey..i try editing mine but a message pops up saying 

```
can't open file to write
```

---

### Post by mali2297 on 2009-10-14
> **abdusamed said:**
> hey..i try editing mine but a message pops up saying 

```
can't open file to write
```

You do not have sufficient privileges as an ordinary user. Try opening the file as a superuser with the command
```

gksudo mousepad /etc/X11/xorg.conf

```

---

### Post by abdusamed on 2009-10-15
wow..it worked..i was able to save the new data.. thankx.. now to check if the trick works or not

---

### Post by inearlygaveup on 2009-10-27
?? My xorg.conf file is empty ??  Any idea's

---

### Post by quimkaos on 2009-10-27
empty?
but do you have any problem with it beeing empty?

if so try:
-sudo dpkg-reconfigure -phigh xserver-xorg
OR
- sudo gnome-display-properties (and save the setings)
OR
-  pasting this using something like < sudo gedit > and then opening the file (it will be writeble):

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
Option "metamodes" "1280x800_60 +0+0"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"ati"
EndSection

---

### Post by inearlygaveup on 2009-10-27
thanks for your help - non of the above worked.
I don't have a problem with it being empty, I was trying to find a way of keeping my resolution settings as they keep changing each time I reboot.

---

### Post by inearlygaveup on 2009-10-27
Sorted - re-installed Xubuntu it then picked up correct Screen resolution settings.

---

### Post by kswenson on 2010-12-08
The fix in this thread worked for me:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1242804&page=4](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1242804&page=4)

---

