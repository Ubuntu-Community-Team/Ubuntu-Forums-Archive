---
title: "Compiz won't work on 7.10"
date: 2008-01-24
forum: Desktop Effects &amp; Customization
---

### Post by fourthdimension on 2008-01-24
Hey All

I can't get compiz fusion / desktop effects working on my 7.10 install.  They worked fine on 7.04.  When I try to enable them, all I get is "desktop effects could not be enabled".  I tried installing xgl, and I was able to get wobbly windows, but I could no longer use a decent resolution or refresh rate, so I uninstalled it.  I have a nvidia graphics card, with what I believe is the proper driver installed.  Can anyone help me?
Thanks.

---

### Post by Ub1476 on 2008-01-24
Post the output of:

```
lspci | grep VGA

compiz
```

---

### Post by fourthdimension on 2008-01-24
```
my_machine~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)
my_machine:~$ 
my_machine:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0111 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

```

---

