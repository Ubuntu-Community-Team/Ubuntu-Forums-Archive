---
title: "Compiz on 710 xgl"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by jgaffney73 on 2008-02-09
Greetings,

I am trying to get compiz to work on a kubuntu 710.  I recievet this error when running compiz --replace

```
mypc@kubuntu:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:0174 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present.
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity
```

I then found this post which seems to be the fix.
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

But it says "Do NOT follow this guide for Gutsy Gibbon 7.10 since Xgl framework has changed dramatically."
So, how do I get xgl to work with 710? or is there another way to fix the above error?

Thank you.

---

### Post by johnnybravo666 on 2008-02-09
Looks like you don't have enough video ram. Compiz needs a minimum of 64mb.
If your card has 64mb of ram then try these tutorials: 
[http://wiki.compiz-fusion.org/Hardware/NVIDIA](http://wiki.compiz-fusion.org/Hardware/NVIDIA) and 
[http://wiki.compiz-fusion.org/Setup](http://wiki.compiz-fusion.org/Setup)

Note: If you're using the proprietary nvidia driver, don't install xgl.

---

