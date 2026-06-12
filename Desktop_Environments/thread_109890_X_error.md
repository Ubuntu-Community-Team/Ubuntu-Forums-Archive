---
title: "X error"
date: 2005-12-29
forum: Desktop Environments
---

### Post by thekiller on 2005-12-29
hello all, 

i was playin with "xcompmgr" and changed my xorg.conf but in the process my "nedit" doesnt seem to work. When i try to open it on a terminal, this is what i get :

```

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  70 (X_PolyFillRectangle)
  Serial number of failed request:  312
  Current serial number in output stream:  322

```

I tried to look around for this error, cos im more of a reader than a poster (can see this is actually my first post, lol) Anyway, thanks in advance and wish u all a prosperous new year !

And just in case if someone needs to see my xorg.conf, here are the sections i changed for xcompmgr :

```

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9000 M9 (R250 Lf)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option 		"AccelMethod" 		"EXA"
	Option 		"AGPMode" 		"4"
	Option 		"EnablePageFlip" 	"true"
	Option 		"DDCMode"
	Option 		"RenderAccel"		"true"
	Option 		"SubPixelOrder" 	"NONE"
	Option 		"ColorTiling" 		"false"
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

---

### Post by thekiller on 2005-12-29
well i just took off the extensions section for composites, and nedit seems to open just fine. However i dont wanna use composites 'cos it awfully slows down my laptop, still i wonder why only nedit seem to hate composites ? gedit, kedit and all other editors open up just fine.

---

