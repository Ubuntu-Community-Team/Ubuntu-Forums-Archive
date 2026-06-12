---
title: "compiz Segmentation fault"
date: 2009-09-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wardy277 on 2009-09-01
Hi,

I have a Dell Studio and i cannot get compiz working. I have a 256 MB ATI Radeon HD 3650  and installed the restricted drivers and even tried installing the drivers from the amd site. I have metacity running in composite mode fine. 

when i run compiz i get:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x900) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
inotify_add_watch: No such file or directory
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (bicubic) - Fatal: GL_ARB_texture_float not supported. This can lead to visual artifacts.

```
i can see compiz working now for a few seconds then:
```

Segmentation fault

```


I have tried completely removing compiz and reinstalling it but i stil lget the error. I dont know if it helps but when i do see compiz running, the window decorations is dark grey where the transparency should be, but not on my awn. I also cannot get any sound out of it but that is a different matter.

here is my spec:
Ubuntu 8.10 (jaunty had networking problems)
Studio Desktop 540MT : Intel Core 2 Quad-Core Q8200 (2.33GHz,1333MHz,4MB) 
3GB RAM
256 MB ATI Radeon HD 3650

(this model disnt have the option to have dell ubuntu, wil lthe dell's versino of ubuntu work for me?)

---

