---
title: "after enabling xgl, 'Available layouts' in keyboard options is EMPTY"
date: 2006-09-23
forum: Desktop Environments
---

### Post by hotani on 2006-09-23
I use Dvorak and now nothing is available. 

?????

---

### Post by hotani on 2006-09-23
Found it in the 'troubleshooting' guide no less... (der.)

from [this page](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit#Installing_XGL.2FCompiz):


> 
"I have no keyboards listed in gnome-keyboard-preferences?"

Firstly, gnome-keyboard-preferences is normally accessed via the System Menu (on your gnome-panel) (system>preferences>keyboard>Layouts Tab).

If you see no keyboards listed (which will effect your alt and windows keys) check your /etc/X11/xorg.conf to make sure you are not using the Xkb extension. Look for the following line in the "Section Modules"

load "xkb"

If you have that line you need to make a change to /etc/gdm/gdm.conf-custom as follows:

Replace

```

command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo -kb

```
with
```

command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo

```


---

