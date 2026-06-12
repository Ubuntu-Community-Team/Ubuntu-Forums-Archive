---
title: "Panels and wallpaper problems"
date: 2008-03-11
forum: Desktop Effects &amp; Customization
---

### Post by applehead on 2008-03-11
Hi all.
I followed this guide
[http://ubuntuforums.org/showthread.php?t=659282]("http://ubuntuforums.org/showthread.php?t=659282")

Now , I think I want to undo it all but don't know how...

the problem with the panels is that the window list doesn't work properly at all. I can only maximise the first window.

the problem with the wallpaper is: when I switch on my pc, I get no panels and the old wallpaper, that is until I wobble the mouse quite a lot then it suddenly comes to life the way I want it and it's ok for a while. until, every so often,  the window decorator disappears and I have to use the file menu to quit an application.

I just wanted the windows to lift off the desktop on rotate and maybe more than one wallpaper.

anyone help please?

Thanks in advance.

---

### Post by sammywham on 2008-03-11
open terminal and type compiz --replace 
what does it show?

---

### Post by applehead on 2008-03-11
> **sammywham said:**
> open terminal and type compiz --replace 
what does it show?

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by sammywham on 2008-03-11
open compiz fusion settings and disable the installations that you just did except screensaver and disable video what happens?

---

### Post by applehead on 2008-03-11
I haven't got much enabled really. all the ones that I didn't have before following the guide are disabled. As I type, I have no window decorator or window list.

---

### Post by applehead on 2008-03-13
I've dsiabled a few more things and every thing seems fine for now so I'll just leave it at that and not touch anything.

Thanks all.

---

### Post by applehead on 2008-03-19
It's no good.  I'm still having all kinds oft problems and I miss having the odd icon on the desktop. 

I've tried unchecking emerald in system - sessions and re starting...  no joy.

Can anyone help me get my system back to the way it is with a new install, without having to do that?

many thanks.

---

