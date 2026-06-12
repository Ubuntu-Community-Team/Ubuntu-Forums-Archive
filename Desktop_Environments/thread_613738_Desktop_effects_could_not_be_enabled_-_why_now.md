---
title: "Desktop effects could not be enabled - why now?"
date: 2007-11-15
forum: Desktop Environments
---

### Post by jamyskis on 2007-11-15
Hi everyone,

Yesterday my 3D effects just stopped working. Well, not strictly stopped working. They had been working very well in Feisty and in Gutsy for quite some time before the Appearance applet suddently started reporting that "Desktop effects could not be enabled". The funny thing is, it enables 3D effects for a few seconds before reverting to the non-3D desktop. I have an Intel 945 chipset and am using the intel driver.

Typing compiz in the terminal brings up:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

Can anyone offer assistance? Thanks!

---

### Post by Sqwishy on 2007-11-15
...Maybe... you need aiglx :S not sure but you could try doing the following to fix it

```
sudo gedit /etc/X11/xorg.conf
```
Look down some till you find a "ServerLayout" section and put in
```
Option "AIGLX" "true" 
```

Then save your stuff and restart X by pressing ctrl+alt+backspace

---

### Post by greatbird451 on 2008-07-24
I have almost the same problem, I have been using "extra effects" for quite a while until recently when it didn't work after reseting my graphics card from a fatal error after overheating on my bed (which was the first time that ever happened). So I'm not too sure what happened, but I think it turned it off by reseting the graphics card. So if anyone can help that would be GREAT. Btw, I started Linux not too long ago, so I don't know a lot of terms; but standard terms are fine.

---

