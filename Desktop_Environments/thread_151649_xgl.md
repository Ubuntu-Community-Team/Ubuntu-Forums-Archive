---
title: "xgl?"
date: 2006-03-28
forum: Desktop Environments
---

### Post by Monque on 2006-03-28
when trying to run 3d apps i get this error message```
Xlib:  extension "GLX" missing on display ":0.0".

```

i looked in synaptic an it was there. any ideas?

---

### Post by christhemonkey on 2006-03-28
What graphics card have you got?
What programs are you trying to run?
What is the ouput of ```
glxinfo
```
Xgl and GLX are different things by the way.

---

### Post by Monque on 2006-03-28
i realised that just after hitting post...

but i have a nvidia card, im trying to run blender, or wings 3d not even cube would run heres my glxinfo :```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Segmentation fault

```

---

### Post by art on 2006-03-28
Do you have glx loaded in your /etc/X11/xorg.conf?

---

### Post by Monque on 2006-03-28
yep, i'm guessing that is this bit :```

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
```

---

### Post by art on 2006-03-28
Do you have GLX in the output of xdpyinfo?

---

### Post by rattking on 2006-03-28
in xorg.conf under the "Device" section witch driver are you loading? nvidia or nv
Driver          "nvidia"
is what you want for glx

---

### Post by Monque on 2006-03-28
[QUOTE=art]Do you have GLX in the output of xdpyinfo?[/QUOTE]
no
[QUOTE=rattking]in xorg.conf under the "Device" section witch driver are you loading? nvidia or nv
Driver          "nvidia"
is what you want for glx[/QUOTE]
changed it to "nvidia"

---

### Post by rattking on 2006-03-28
OK that's probably the gl problem.. you will want to be sure the closed source drivers are installed 
basically its
sudo apt-get install nvidia-glx linux-restricted-modules-yourkernel

linux-restricted-modules-2.6.12-10-386 linux-restricted-modules-2.6.12-10-686 linux-restricted-modules-2.6.12-10-k7 are your options
here is the official howto
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

does glxinfo still Segmentation fault?

---

### Post by Monque on 2006-03-28
got it working. turns out i needed the legacy drivers thanks for all the help, thats what is great about ubuntu you always get the help you need.

---

