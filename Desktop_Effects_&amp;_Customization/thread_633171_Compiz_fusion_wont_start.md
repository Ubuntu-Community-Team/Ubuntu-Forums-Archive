---
title: "Compiz fusion wont start"
date: 2007-12-06
forum: Desktop Effects &amp; Customization
---

### Post by Hawk__0 on 2007-12-06
I compiled all the compiz-fusion stuff from source, then when it randomly crashed on me (which was 0.6.2/o.6.0) i decided to uninstall it, and install from the package mananger.  i did so, i see compiz fusion load up (the desktops increase to 4 from 2), then it crashes back to metacisty.  terminal output:
```
steve@steve:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
Segmentation fault (core dumped)

```
I suspect it is something to do with emerald since i cannot start emerald.
if i try this: emerald --replace, it does nothing, and the command line just sits there until i control+c it.

---

