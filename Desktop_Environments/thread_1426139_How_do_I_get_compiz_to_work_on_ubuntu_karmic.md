---
title: "How do I get compiz to work on ubuntu karmic"
date: 2010-03-09
forum: Desktop Environments
---

### Post by fivex on 2010-03-09
I have all 3 DEs installed. I have read and read, but I can' figure out how to get compiz to work on xfce. Help?

---

### Post by finlost on 2010-03-09
Kind of hard to solve the problem when you don't list the issues.  Its like saying your car is broke.  Just sayin'....

---

### Post by andrea000 on 2010-03-09
Have you installed compiz config settings manager yet?
system->administration->synaptic package manager
and look for compizconfig setting manager or from the
terminal
> sudo apt-get install compizconfig-settings-manager

Edit I forgot you said you are running xfce but it's still
the same in the terminal and it will be in the package
manager also.

---

### Post by fivex on 2010-03-09
> **andrea000 said:**
> Have you installed compiz config settings manager yet?
system->administration->synaptic package manager
and look for compizconfig setting manager or from the
terminal


Edit I forgot you said you are running xfce but it's still
the same in the terminal and it will be in the package
manager also.

I have done that. But nothing works from it. It works in gnome, but not xcfe.

---

### Post by andrea000 on 2010-03-09
Did you set it up animations and everything like that
and set your visual effects to extra?
if not right click on the desktop click change desktop
background click on the visual effects tab and see if
it works if not go to the terminal and type compiz in
and post the output.

---

### Post by BenAshton24 on 2010-03-09
```
compiz --replace
```
?

---

### Post by fivex on 2010-03-10
> **andrea000 said:**
> Did you set it up animations and everything like that
and set your visual effects to extra?
if not right click on the desktop click change desktop
background click on the visual effects tab and see if
it works if not go to the terminal and type compiz in
and post the output.

Running the command compiz seemed to start it up
Is there any way to get compiz to start after logging in?
And compiz's output(It's apparently still outputting stuff, it's just taking a very long time to do so)
```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1440x795) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
OpenGL Warning: No pincher, please call crStateSetCurrentPointers() in your SPU
OpenGL Info: Using XSHM for GLX_EXT_texture_from_pixmap
Couldn't find a perfect decorator match; trying all decorators
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
OpenGL Warning: No pincher, please call crStateSetCurrentPointers() in your SPU
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

```

---

### Post by BenAshton24 on 2010-03-10
> **fivex said:**
> Is there any way to get compiz to start after logging in?

if I understand your question correctly then this should do it...
```
compiz --replace
```

---

### Post by Barriehie on 2010-03-10
After you do:
```

compiz --replace
``` as posted above you have to save the session.

---

### Post by fivex on 2010-03-10
Thank you. Now I just have to wait for compiz to run through it's output again and then I will save the session.
Again, thank you.

---

