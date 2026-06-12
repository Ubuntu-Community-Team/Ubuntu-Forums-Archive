---
title: "Compiz Problems: XGL not present"
date: 2008-04-19
forum: Desktop Effects &amp; Customization
---

### Post by Tha3xampler on 2008-04-19
I have recently installed the nVidia driver(nvidia-glx). I seem to have problems starting up compiz.However, I can run the other standard stuff such as glxgears.

Info: 
glxinfo | grep direct: direct rendering: Yes

compiz: 

Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:01d8 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: not present.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting

---

### Post by Zorael on 2008-04-19
Curious.


You don't want XGL with Nvidia cards, so no worries.

Do you have the needed options added to your xorg.conf file? Else run this command in a terminal.
```
$ sudo nvidia-xconfig -d 24 --allow-glx-with-composite --add-argb-glx-visuals --composite *--randr-rotation --render-accel*
```

Parts in italics are optional, but I recommend them.

---

### Post by Tha3xampler on 2008-04-19
This fixes the problem. But now, when I launch compiz. My window bar and my taskbar disppear.

---

### Post by Zorael on 2008-04-20
Clarify some things for me, please.

Window bar, as in, titlebars and borders on windows? If so, you're not running a window decorator. There are others, but try Emerald first; package name **emerald**. Install it through Synaptic or via a terminal.
```
$ sudo aptitude install emerald
```


Taskbar, as in, the gnome panel? If so, we could forcefully kill it and restart it.
```
$ compiz --replace --loose-binding &

*<wait until compiz loads and proceed if the panel disappeared>*

$ killall gnome-panel
$ gnome-panel &
```

If that fixes things we could make it into a script.

---

