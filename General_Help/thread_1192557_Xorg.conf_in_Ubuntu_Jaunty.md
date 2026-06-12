---
title: "Xorg.conf in Ubuntu Jaunty"
date: 2009-06-20
forum: General Help
---

### Post by hal8000 on 2009-06-20
Things appear to have changed much in Jaunty, heres my /etc/X11/xorg.conf cat /etc/X11/xorg.conf

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"False"
EndSection


So where does Jaunty get information about the default resolution to use, keyboard layout and mouse driver, etc.
The xorg.conf used to be much larger and contain all these settings,
Thanks in advance.

---

### Post by Ayuthia on 2009-06-20
All if the information is detected by hal so the configuration can be found in /usr/share/hal/fdi/policy.  If I remember correctly though, if you want to make changes you should copy that file into /etc/hal/fdi/policy so that it does not get wiped out on future hal updates.

---

### Post by hal8000 on 2009-06-20
Thanks a lot, I'll have a look at that file and save that info for future reference.

---

