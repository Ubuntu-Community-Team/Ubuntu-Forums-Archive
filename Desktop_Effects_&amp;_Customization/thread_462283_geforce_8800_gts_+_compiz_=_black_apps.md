---
title: "geforce 8800 gts + compiz = black apps"
date: 2007-06-02
forum: Desktop Effects &amp; Customization
---

### Post by Zodiaq on 2007-06-02
Ok, I'm a bit new to Ubuntu but managed to configure compiz... tested beryl... have problems with both - after some time using compiz app starts to show only black color inside window - no buttons/controls visible... but systems doesn't hung - if I point in right place can close apps... only way to get app working again is to disable compiz (desktop effects)...

here is my xorg.conf (only device and module sections):

```

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dbe"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection
Section "Device"
	Identifier	"Device"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Busid		"PCI:1:0:0"
	Option		"RenderAccel" "true"
	Option		"AllowGLXWithComposite" "true"
	Option		"Coolbits" "1"
	Option		"AddARGBVisuals"	"true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"NoLogo"		"true"
EndSection

```

---

### Post by Jarcon on 2007-06-03
I am having the same problem when I enable desktop effects in 7.04.  I have an older dell laptop with a nvidia gforce2go card in it.

xorg.conf
```

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV11 [GeForce2 Go]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

```

---

### Post by Zodiaq on 2007-06-07
big thx for help guys

---

