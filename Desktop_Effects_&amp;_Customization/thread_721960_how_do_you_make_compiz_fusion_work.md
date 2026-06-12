---
title: "how do you make compiz fusion work?"
date: 2008-03-11
forum: Desktop Effects &amp; Customization
---

### Post by pidgeon on 2008-03-11
i can't figure it out. i think i have it installed. i installed all the packages, but, i can't figure it out from here. i put compiz --replace into a terminal and got this:

leapfrog@lilypad:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 02:00.0 0300: 10de:0343 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure


what's it mean?

---

### Post by itix on 2008-03-11
Why don't just use the synaptic package manager to check if you have it installed. If you DO have it installed, a good thing to have is compizconfig-settings-manager aka ccsm. You can it as well in the Synaptic Package manager.

---

### Post by pidgeon on 2008-03-11
they're all installed, but, i can't find the ccsm package

---

### Post by Afkpuz on 2008-03-11
Are you using an ATI video card?  If so, you need to install xserver-xgl to run compiz

```
sudo apt-get install xserver-xgl
```

---

### Post by itix on 2008-03-11
Misspelled it... I have edited my previous post now. Try again.

---

### Post by pidgeon on 2008-03-11
it says couldn't find package xserver-xgl

---

### Post by pidgeon on 2008-03-11
i have an nvidia nforce video card

---

### Post by itix on 2008-03-11
Have you found compizconfig-settings-manager yet?

---

### Post by pidgeon on 2008-03-11
okay, i installed the xserver-xgl, and i ran the compiz --replace command again and the same thing popped up i think.

leapfrog@lilypad:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 02:00.0 0300: 10de:0343 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (wall) - Error: Couldn't create cairo context for switcher
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure

---

### Post by pidgeon on 2008-03-11
i found the compizconfig package and am in the process of installing it, i'll update momentarily.

---

### Post by pidgeon on 2008-03-11
okay, so, i got the effects kind of working, i just don't know how to use them.

---

### Post by itix on 2008-03-12
*The cube is activated witk ctrl + alt + mouse-button-1. (you'll need desktop cube activated and desktop wall de-activated in ccsm)

*ring switcher is a good plugin which can be activated in ccsm. I've assigned super (windows button) + n for next on all desktops and super + m for backwards. 

*Water effects is a rather meaningless plugin, but it's a good laugh. Activate rain with shift + F9

You can play forever with the various plugins for compiz-fusion.

---

### Post by pidgeon on 2008-03-12
thanks. i'm kinda figuring it out. i'm still trying to figure out how to activate the animations. it won't stay activated,

---

