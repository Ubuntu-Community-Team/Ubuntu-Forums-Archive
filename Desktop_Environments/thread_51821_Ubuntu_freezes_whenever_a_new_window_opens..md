---
title: "Ubuntu freezes whenever a new window opens."
date: 2005-07-25
forum: Desktop Environments
---

### Post by Dural on 2005-07-25
My brother and I have just installed Ubuntu on our hard drive (for some strange reason, we couldn't access our Kubuntu install anymore through the BIOS, so we reformated and installed Ubuntu instead). Everything generally works fine, except that whenever a new window is opened, Ubuntu freezes and we have to reset the computer. We can not figure out how this keeps happening, particularly in the screensaver section of GNOME. Is there a way to fix this problem? 

Basic Specs:
Processor: AMD Sempron 3100+
HD running Linux: Maxtor 6Y8000 (80 GB)
Memory total: 1 GB
Video Card: Radeon 8500LE 64MB
Motherboard: MSI K8T Neo

---

### Post by danns on 2005-07-25
This could be a video driver issue.  Can you  reproduce the problem consistently by opening up the screensaver configuration?  If so, is it a specific screen saver?  Could it quite possible be an OpenGL based screensaver?

---

### Post by Dural on 2005-07-25
[QUOTE=danns]This could be a video driver issue.  Can you  reproduce the problem consistently by opening up the screensaver configuration?  If so, is it a specific screen saver?  Could it quite possible be an OpenGL based screensaver?[/QUOTE]

Yes, that was were the problem occurred. It seems to happen more with the 3D (OpenGL-based) screensavers. I just got it to freeze by loading Euphoria, which uses OpenGL. My brother mentioned that it froze once when he exited Gnometris (sp?).

---

