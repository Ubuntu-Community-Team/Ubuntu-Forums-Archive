---
title: "compiz fusion on nvidia problems"
date: 2008-01-26
forum: Desktop Effects &amp; Customization
---

### Post by fourthdimension on 2008-01-26
I have 7.10, and I installed compiz fusion from the guide on the ubuntu wiki, but I can't get it to work with my nvidia card.  I get this message:
```
my_machine:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0111 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 
```
Compiz Fusion worked on all the previous installs, so I know my hardware supports it.  Can anyone tell me how to fix this problem?
Thanks.

---

### Post by fourthdimension on 2008-01-26
Update - I commented out the line in the nvidia configuration file that checked the video memory, so now I can run compiz, but I get black and white windows only.  I ran it with this:
```
compiz --replace --indirect-rendering --loose-binding
```
but then I get just white windows... nothing shows up in any of my folders or anything.

---

