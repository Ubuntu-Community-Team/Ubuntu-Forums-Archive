---
title: "Compiz broken after patching fresh install of Gusty"
date: 2007-12-02
forum: Desktop Effects &amp; Customization
---

### Post by killerasp on 2007-12-02
I am running intel p4 with nvidia 6800GT. Compiz was working properly with restricted drivers but stopped working after performing a system update. 

Here is an output of compiz --replace

andrewy@andrewy-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:00f1 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (3200x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
Segmentation fault (core dumped)

there is nothing else after the last line in the output. 

Any help or suggestions would be great. Been stuck with this all day.

---

### Post by reverend_HH on 2007-12-02
i had an update mess up my graphics drivers not too long ago so what you'll want to try is to reinstall them and go from there.

---

