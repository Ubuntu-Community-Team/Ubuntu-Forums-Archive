---
title: "Compiz and visual affects don't work."
date: 2009-09-19
forum: Desktop Environments
---

### Post by GroogFish on 2009-09-19
I have NVidia GeForce 8400gs with driver- NVidia Accelerated Graphics Driver (version 180).
When I try and enable visual affects the screen blinks a few times and it says "Desktop effects could not be enabled."

What should I do to fix this?

---

### Post by ultimatebuster on 2009-09-19
ARe you sure you have the **Proper** drivers installed? For me it was the missing -hd in the end (I have an ATI HD Card)

---

### Post by GroogFish on 2009-09-19
The only two drivers that show up in my Hardware Drivers are
-NVIDIA accelerated graphics driver (version 180) [recommended]
-NVIDIA accelerated graphics driver (version 170)

---

### Post by Admiral Yi on 2009-09-20
Which one is selected (has a green dot on the left)? If its the bottom one, I'd suggest installing the recommended one. If neither, then there's your problem.

---

### Post by GroogFish on 2009-09-20
I've installed the recommended driver, but when I try to start compiz I see this-

> micah@micah-comp:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0


---

