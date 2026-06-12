---
title: "[SOLVED] Desktop effects not working after resolution change"
date: 2007-11-13
forum: Desktop Environments
---

### Post by oudalrich on 2007-11-13
Hello,

I have a Lenovo T60 with a 1024x768 LCD and Intel GMA 950 graphics. It is connected to a 23" Apple Cinema Display. The latter has a native resolution of 1920x1200.

I had some trouble setting the resolution to 1900x1200. The "Screens and graphics" thing in Administration would not let me select anything higher than 1280x800, neither did xrandr. "Screen resolution" in Preferences, however, did. So far, so good, But now desktop effects do not work any more, even at 1024x768. When I turn them on in Preferences/Appearance, I get an error saying "Desktop effects could not be enabled", and that's it. This is the output of compiz, in case it's any help:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

Thank you for your answers in advance,

Uli

---

### Post by betes on 2007-11-14
i have the exact same problem

Searching the forums, this thread might describe the same problem (its not clear):

[http://ubuntuforums.org/showthread.php?t=494194&highlight=desktop+effects+resolution](http://ubuntuforums.org/showthread.php?t=494194&highlight=desktop+effects+resolution)

---

### Post by betes on 2007-11-14
Okay- After a reboot Desktop effects were still disabled, but I was able to turn them on in prefs/appearance without getting the error message...

So I don't have the problem anymore, but does anyone know why adjusting resolution would disable them in the first place?

---

### Post by oudalrich on 2007-11-14
I solved the problem too, with a simple
```
sudo dpkg-reconfigure xserver-xorg
```
Now I'm back to square one and have to figure out a way to adjust the screen resolution without messing things up. I am working on another external monitor right now, with a resolution of 1680x1050 instead of the CinemaDisplays's 1900x1200. No problem this time.

Like betes, I would really be interested in knowing what went wrong the first time. In fact, there were more problems than just the disabled desktop effects, x.org crashed several times.

Also, I'd really like to know why there are two graphical interfaces for setting the screen resolution, one not working properly and the other causing crashes. (Oh wait, this is Linux, that's just the way things are done here.)

---

