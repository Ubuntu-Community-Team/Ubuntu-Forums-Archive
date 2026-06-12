---
title: "Need help with Compiz Fusion and Geforce 2"
date: 2007-11-25
forum: Desktop Effects &amp; Customization
---

### Post by Codename46 on 2007-11-25
Ok, here's the error message:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:07.0 0300: 10de:0110 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

Do I HAVE to have a 64-meg video card? I could have sworn I've seen people get Compiz-Fusion working with 32-meg cards.

I am using a Geforce 2 MX 400. Any solution to this problem? I really would like Compiz-Fusion to work. Thanks.

---

### Post by Forlong on 2007-11-25
Your graphics card has too less memory to run Compiz *properly* (which doesn't mean it won't be able to do it at all).
If still want to use it, try this:
```
SKIP_CHECKS=yes compiz
```

---

