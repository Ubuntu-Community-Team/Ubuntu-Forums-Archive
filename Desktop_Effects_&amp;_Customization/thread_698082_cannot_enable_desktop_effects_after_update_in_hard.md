---
title: "cannot enable desktop effects after update in hardy!!!"
date: 2008-02-15
forum: Desktop Effects &amp; Customization
---

### Post by theproc64 on 2008-02-15
I have a desktop with a geforce fx 5200 with 128 mb of graphics ram.  It was running desktop effects great and gutsy and great after I upgraded to hardy but this update seems to have done something.  I also removed the package mythtv along with a few other packages but reinstalling it and all its dependencies doesn't seem to help.

proctopus@harold:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 


proctopus@harold:~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

---

### Post by Anduu on 2008-02-16
Hardy related questions should be posted here [http://ubuntuforums.org/forumdisplay.php?f=305](http://ubuntuforums.org/forumdisplay.php?f=305)

---

