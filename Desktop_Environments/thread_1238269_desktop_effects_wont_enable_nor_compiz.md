---
title: "desktop effects wont enable nor compiz"
date: 2009-08-12
forum: Desktop Environments
---

### Post by andru183 on 2009-08-12
i cant get my desktop effects to go from off to normal/extra or compiz to run, if i launch compiz out of the terminal i get this

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 455: /usr/bin/compiz.real: not found

i see i say something arent there but i dont know where to get them from and im sure my nvidia drivers are up to date as per the hardware manager but sumits amiss

---

### Post by AmerNewbieInDE on 2009-08-12
what card you useing

---

### Post by andru183 on 2009-08-12
> **AmerNewbieInDE said:**
> what card you useing

nvidia 8800 gt 1Gb

---

### Post by AmerNewbieInDE on 2009-08-12
first, i would check nvidia, for new linus drivers for your card. it was tricky, but i got mine installed and am very happy, then...

besides enabling your desktop settings, you must also enable/install  Compiz..

also for settings...first, you need, Desktop (in compizConfig Settings) desktop cube and rotate cube enabled, then Effects, you need 3D windows, if you want a sphere or cylinder, also Cube Reflections and Deformations enabled. Then back at the main window under `General` General Options..Desktop size tab, horizontal virtual size = 4, vertical virtual size = 1, number of desktops = 4, back out, close and enjoy.. use ctrl, alt and button one of mouse... ove mouse side to side to move where you want.

---

