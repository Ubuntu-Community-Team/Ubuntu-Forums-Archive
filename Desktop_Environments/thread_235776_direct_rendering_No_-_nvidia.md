---
title: "direct rendering: No - nvidia"
date: 2006-08-13
forum: Desktop Environments
---

### Post by distroman on 2006-08-13
ubuntu dapper
Geforce FX 5200
Installed -
nvidia-kernel-common
nvidia-glx

```
distro@ubuntu2001:~$ glxinfo | grep direct
direct rendering: No
```

Should it not be on? I think it use be.

/etc/X11/xorg.conf
```
Section "Module"
	#Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
```

```
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
	Option 		"RenderAccel" 		"true" 
	Option 		"AllowGLXWithComposite" "true"
```

Maybe I should say that this was originaly a Ubuntu 5.10 _Breezy Badger. 
Could it have broken some where a long the way? I would not have noticed, but I need 3D now.
What should I do?

Thanks

edit
> XGL doesn't support direct rendering but it uses accelerated indirect rendering. If you want direct rendering figure out at which 'display' the host Xserver is running and connect to it by adjusting the DISPLAY variable.

In case of AIGLX you can get direct rendering but as you know the nvidia drivers don't support it yet (missing texture_from_pixmap).

ohhh got xgl/compiz,,,
guess I am not supose to have direct rendering.

---

