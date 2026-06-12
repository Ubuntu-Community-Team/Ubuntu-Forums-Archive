---
title: "Error after installing compiz"
date: 2007-10-05
forum: Desktop Effects &amp; Customization
---

### Post by olymp on 2007-10-05
I went to start up compiz fusion, which i just installed. This error resulted.What did i do wrong and how do I fix it?

pxxxx@pxxxx:~$ compiz --replace emerald
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0392 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
pxxxx@pxxxx:~$

---

### Post by Forlong on 2007-10-05
> **olymp said:**
> Checking for Composite extension: not present.
Post the output of:
```
grep -v ^# /etc/X11/xorg.conf
```
and please use the forum's CODE tag (# button)

---

