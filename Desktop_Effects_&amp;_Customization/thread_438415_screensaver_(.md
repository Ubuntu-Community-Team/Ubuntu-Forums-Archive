---
title: "screensaver :("
date: 2007-05-09
forum: Desktop Effects &amp; Customization
---

### Post by Orfeus on 2007-05-09
When i m trying to preview some of the screen savers i cannot get them work properly. It seems like a graphics card problem. I m pretty sure that i ve install my card drivers. Any ideas?

---

### Post by Ateo on 2007-05-09
1. what kind of card ?
2. what screen savers? openGL or non?

Regards

---

### Post by Orfeus on 2007-05-10
It s a Nvidea 7600. I think it's only with the open Gl

---

### Post by mcduck on 2007-05-10
Sounds like your graphics drivers are not working correctly.
What does running 'glxinfo | grep direct' say?

---

### Post by Orfeus on 2007-05-14
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

---

### Post by Cresho on 2007-05-15
easy!

first off, install correct drivers.

sudo apt-get install nvidia-glx nvidia-kernel-common

secondly,

sudo dpkg-reconfigure xserver-xorg

---

### Post by misfitpierce on 2007-05-15
For me they only work when in XGL session perfectly, but under regular gnome they lag just a hair

---

### Post by Orfeus on 2007-05-21
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

I typed the first thing you wrote and i keep getting this

---

### Post by Orfeus on 2007-06-17
When i write glxinfo | grep direct i get this

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


Is it ok?

---

