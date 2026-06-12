---
title: "Strange problem with compiz"
date: 2009-01-19
forum: General Help
---

### Post by Aspras on 2009-01-19
I am encountering a strange problem I never have before. Whenever I do "compiz --replace" I get this output :

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Segmentation fault
/home/paul/.themes/Pucko Modern Blue/gtk-2.0/gtkrc:482: error: invalid string constant "panel", expected valid string constant


Because of this Compiz Fusion Icon doesnt seem to work correctly either. I believe this happened because this time I installed compiz before my graphics card's drivers. Any suggestions?

---

### Post by lykwydchykyn on 2009-01-19
Try creating a new user, and log in to that fresh account.  See if compiz works in that account.  If it does, you probably just have a corrupt compiz configuration.  If it doesn't, it's more likely an issue with the video card driver.

---

### Post by gettinoriginal on 2009-01-19
Ok, have to start somewhere, so first, is your driver enabled ??  System > Administration > Hardware Drivers.  Second, System > Preferences > Appearance > Visual Effects > Extra or Custom.

---

### Post by Aspras on 2009-01-20
Drivers are activated, Visual Effects are set to None.

---

### Post by gettinoriginal on 2009-01-20
Visual Effects have to be set to Extra or Custom. :p

---

