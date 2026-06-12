---
title: "this wierd :))"
date: 2007-10-16
forum: Desktop Effects &amp; Customization
---

### Post by Myronray on 2007-10-16
hello to all ubuntu experts need some help here, i successfuly intall my nvidia driver but when i run firefox there is no maximized and close menu at the rightside of firefox explorer and also i cannot drag any open application and the way is to close in panel... plsss help

---

### Post by luisfpg on 2007-10-16
Looks like there's no active window decorator...
If you're running gnome, press alt+F2 and type **metacity --replace**
If kde, run **kwin --replace**
Perhaps it's a compiz misconfiguration...

---

### Post by bubbalouie on 2007-10-16
If you are using a composite desktop a misconfigured xorg.conf  file could cause this, if so you have two options:

1) Disable composite desktop

2) Edit the /etc/X11/xorg.conf file the section in bold is the important bit (from memory sorry, so hopefully someone can help confirm, either way back it up before hand)

> Section "Device"
	Identifier	"nVidia Corporation G72M [GeForce Go 7400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	**Option		"AddARGBGLXVisuals"	"True"**
	Option		"NoLogo"	"True"
EndSection

I hope this helps, this has only happened to me once a long time ago when I first played with 3D desktops, if I am a touch scant on details let me know and I will add more detail.

Good luck :)

Ryan

---

