---
title: "Jaunty, compiz, nvidia, Checking for Software Rasterizer: Not present."
date: 2009-06-07
forum: Desktop Environments
---

### Post by szamot83 on 2009-06-07
Hello, 
I have installed Jaunty yesterday, and I'm trying to enable Compiz.

I have Nvidia Graphics (6200) + NVIDIA-Linux-x86-185.18.14 drivers.
When I try to run Compiz in terminal it gives me:
```
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
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
```
This message is repeating all time till I press Ctrl+C.

When I try Compiz-check:
```
 Graphics chip:         nVidia Corporation NV44A [GeForce 6200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [OK ]
 Checking for non power of two support...          [OK ]
 Checking for composite extension...               [OK ]
 Checking for FBConfig...                          [OK ]
 Checking for hardware/setup problems...           [OK ]
```
My xorg.conf [http://files.mint-space.com/getfile,20090607115258,xorg.conf.html](http://files.mint-space.com/getfile,20090607115258,xorg.conf.html)
My Xorg.0.log [http://files.mint-space.com/getfile,20090607115356,Xorg.0.log.html](http://files.mint-space.com/getfile,20090607115356,Xorg.0.log.html)
Where is the problem?
Sorry for my English.
Best regards

---

