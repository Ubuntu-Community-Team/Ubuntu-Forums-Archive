---
title: "3D effects problem."
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by din on 2007-12-27
Hi.
Compiz is enabled. I have some effects working like windows movement .
The problem begins with 3D graphics. 3D effects of compiz not working + when i tried google earth - system is logging out.

lspci | grep  vga  
 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

compiz: 
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

Any ideas ?

---

### Post by Forlong on 2007-12-27
You have to stop Compiz before running 3D apps like google earth. Your graphics chip/driver can't handle both at a time.

Just open [Alt]+[F2] and run ```
metacity --replace
```

---

