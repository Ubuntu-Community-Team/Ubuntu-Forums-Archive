---
title: "Windowed 3D apps and Compiz on Radeon 9200"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by Mr Groch on 2007-11-06
Hello,

I have problem with 3D apps running in widowed mode when Compiz is enabled....
Static 3D image in window is looking OK, but when I try to interact with this window, image
gets flickering. This is very annoying in games and also in apps like 3dearth, becouse
I can't see anything when I want to click maouse inside the window...

In fullscreen apps, all is ok (like OpenArena, America's Army, etc). Disabling
desktop effects solves this problem, but this is not a good solution, I dont want
to manually disable compiz each time, I want to play Chess 3D :/

I have also noticed strange logs after running compiz:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 1002:5960 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
```

Is this OK? I mean "Trying again with indirect rendering:"?
Direct rendering is working, I think...

```
glxinfo | grep direct
direct rendering: Yes
```

---

### Post by amadeus266 on 2007-11-06
I have an ATI AIW 9200 and have the same problem. The card (or should I say it's drivers) just isn't up to snuff with linux. They work great in windows though.

---

### Post by Mr Groch on 2007-11-06
Don't you know if installig closed ATI driver will help?

---

### Post by doggiedoll on 2007-11-10
I think new fglrx 8.42.3 will not help in this case. It is not a driver that support Radeon 9200. I have laptop with Mobility Radeon 9200. I did have a hard time config new fglrx to my system. Then I directly search in ATI.com. The lastest version that supported my mobility radeon is 8.28.8. Sorry it is a bad news.

---

### Post by Mr Groch on 2007-11-11
Yes, I have tried to install fglrx 8.42.3 - no result... X don't run...

```
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.42.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.423.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 19 2007 16:13:26
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found
```

---

### Post by doggiedoll on 2007-11-12
> **Mr Groch said:**
> Yes, I have tried to install fglrx 8.42.3 - no result... X don't run...

```
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.42.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.423.2                  
(II) ATI Proprietary Linux Driver Build Date: Oct 19 2007 16:13:26
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(EE) No devices detected.

Fatal server error:
no screens found
```

Some of our friends here roll back xorg from Gutsy to Feisty which is Xorg 7.2. He got a beautiful result. You can try it. I did not know yet that he just add the *.deb or add the repository and which one to add. I am asking him too.

---

