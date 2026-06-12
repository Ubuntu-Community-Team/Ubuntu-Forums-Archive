---
title: "Slow compiz intel GM965"
date: 2008-12-17
forum: General Help
---

### Post by macav on 2008-12-17
I have a problem with intrepid, that compiz is really slow, for example when I rotate the cube or just move the window, it's slow. I would like to know the reason why it's different than in hardy, in hardy, everything was okay and the performance was smooth. Now I have to stay in hardy and cannot enjoy gnome 2.24 and other features. anybody could give me explanation or advice? I hope in jaunty it will be smooth like in hardy ...

---

### Post by Izek on 2008-12-17
What graphics card do you have?

Also, what's in var/log/xorg.0.log?

---

### Post by macav on 2008-12-17
intel GM965 .. X3100 .. i don't know what's in log, as I said i use hardy instead of intrepid because of the issue.. but as far as I remember the xorg.conf file was default - almost clean, only "intel" driver specified, no more parametres.

---

### Post by densou on 2009-01-04
> **macav said:**
> but as far as I remember the xorg.conf file was default - almost clean, only "intel" driver specified, no more parametres.

please, let me advice to use mine: (it is the best with Intrepid so far) -always do a backup of yours before editing it!-

```
Section "Module"
	Load 	"bitmap"
	Load 	"ddc"
	Load 	"dbe"
	Load 	"dri"
	Load 	"extmod"
	Load 	"freetype"
	Load 	"glx"
	Load	"GLcore"
	Load 	"int10"
	Load 	"type1"
	Load	"v4l"
	Load 	"vbe"
EndSection

Section "Device"
        Identifier 	"intel"
        Driver     	"intel"
        Option          "AccelMethod"   "EXA"
EndSection

Section "Screen"
        Identifier 	"Default Screen"
	Device 		"intel"
EndSection

Section "DRI"
	Mode 	0666
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Option 		"AIGLX" 		"true" 
EndSection

Section "Extensions"
	Option 		"Composite" 		"true"
EndSection
```

---

