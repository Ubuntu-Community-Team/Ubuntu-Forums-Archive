---
title: "Compiz fusion problem"
date: 2009-04-13
forum: General Help
---

### Post by Benbow on 2009-04-13
I have compiz running in Intrepid but am having problems in Jaunty. If I try to run Compiz from the terminal I get the following where it seems that"Xgl" is a problem.
Any ideas?

benbow@benbow-desktop:~$ sudo compiz fusion
[sudo] password for benbow: 
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'fusion'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by tripolitan on 2009-04-13
looks like xgl support is broken for your card or some xgl or mesa packages are not installed. Is this happening on the same machine? or two different machines + Post your hardware info please.

FYI, 9.04 is in alpha or beta testing phase, if you want a production version, I would suggest 8.04 LTS

---

