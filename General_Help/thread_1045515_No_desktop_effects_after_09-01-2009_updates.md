---
title: "No desktop effects after 09-01-2009 updates"
date: 2009-01-20
forum: General Help
---

### Post by perettigiuliano on 2009-01-20
Hi all,
after 09-01-2009 updates (driver?, compiz? i don't know!!!) desktop effects are gone...

this is some output from  commands compiz-related:
giuliano@giuliano-desktop:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
2 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault

But i am sure that driver nvidia 177 are active and in use, as "hardware drivers" windows says.
Someone can help me please???

---

### Post by gettinoriginal on 2009-01-21
There is an "nvidiaglx" in synaptic for older cards, would that apply to you ??

---

### Post by perettigiuliano on 2009-01-23
> **gettinoriginal said:**
> There is an "nvidiaglx" in synaptic for older cards, would that apply to you ??

Oh yes, synaptic says: "nvidia-glx 177 installed"... but nothing

I have noted that there are also 180 driver, well unistall 177 and install 180.... GOT IT!!! It works again!!!

Thanx to all...

---

