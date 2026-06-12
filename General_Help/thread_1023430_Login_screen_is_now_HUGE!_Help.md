---
title: "Login screen is now HUGE! Help"
date: 2008-12-27
forum: General Help
---

### Post by alpwazungy on 2008-12-27
Hi

I upgraded from ubuntu 7.1 to 8.04. So far I have found no problems (fingers crossed) except that the login screen is now about 4x larger than my monitor can show, leaving the text entry box not visible off screen (just off screen to the lower right). As a result I am typing blind to login.

How do I fix this?????

Thanks

Alp

---

### Post by Zorael on 2008-12-28
Open up **/etc/X11/xorg.conf** in a text editor with superuser permissions and comment out (or remove) the line beginning with *Virtual*.
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Card"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	Subsection "Display"
		Depth 24
**_#_**		Virtual 1600 1200
	EndSubsection
EndSection
```

Alternatively just rename the file (to a backup) and have your system regenerate a new one.
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup0812
$ sudo dpkg-reconfigure xserver-xorg -phigh
```

---

### Post by alpwazungy on 2009-01-05
I will try the second option as I feel I MIGHT be able to recover easier if it doesn't work.

Thanks.

---

### Post by alpwazungy on 2009-01-05
Hmmm.... after backing up (mv xorg.conf to xorg.conf-bu)...

 sudo dpkg-reconfigure xserver-xorg -phigh

debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31 columns wide.)
debconf: falling back to frontend: Readline
md5sum: /etc/X11/xorg.conf: No such file or directory

I wonder if it worked.

---

### Post by alpwazungy on 2009-01-05
Fell back to initial recommendation with mod.
Edited xorg.conf to remove rediculously high " virtual 1856  1392" to 1084 768.

MUCH better

Thank you!

---

