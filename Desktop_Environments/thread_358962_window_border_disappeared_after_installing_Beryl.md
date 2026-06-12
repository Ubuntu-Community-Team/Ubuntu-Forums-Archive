---
title: "window border disappeared after installing Beryl"
date: 2007-02-11
forum: Desktop Environments
---

### Post by Glenn Jones on 2007-02-11
Hey,

I've just installed beryl on my Toshiba Satellite laptop.(The guides on the forums were great - cheers guys.here is the link of the one I followed, [http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl+green](http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl+green) ) Unfortunately the maximize/minimize and close window border has disappeared. Can any one help me get this back.

Thanks 
Glenn

---

### Post by Mikael on 2007-02-11
Edit your /etc/X11/xorg.conf and make sure the line below is in the "Screen" section:

	Option		“AddARGBGLXVisuals” “True”

This worked for me.

---

### Post by Tilex on 2007-02-11
When it happened to me, I simply closed the beryl application and re-started it after.  You could also right-click on the beryl taskbar icon and click "Reload Windows Decoration".

---

### Post by Glenn Jones on 2007-02-12
I've tried both your suggestions and they dont seem to work. I tried to open the beryl-manager in the terminal and I get this:

* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32

---

### Post by w1ndow on 2007-02-12
try right clicking beryl-manager icon, advanced beryl options then set rendering path to copy.
this could be wrong as im not by my pc right now, so cant check.

---

### Post by Glenn Jones on 2007-02-12
Sorry to say that didn't work either. The screen goes all green and crazy.

---

### Post by shareMenaPeace on 2007-02-12
Put the default depth to 24 under screen in xorg.conf

---

### Post by Glenn Jones on 2007-02-12
Cheers that did the trick

---

### Post by beefcurry on 2007-02-13
> **w1ndow said:**
> try right clicking beryl-manager icon, advanced beryl options then set rendering path to copy.
this could be wrong as im not by my pc right now, so cant check.

Thanks that worked great for me!

---

