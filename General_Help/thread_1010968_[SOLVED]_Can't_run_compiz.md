---
title: "[SOLVED] Can't run compiz"
date: 2008-12-14
forum: General Help
---

### Post by wersdaluv on 2008-12-14
I have an Intel X3100 graphics hard that has been running Compiz correctly until minutes ago. A while ago, I enabled metacity. When I wanted compiz back, I tried the Appearance dialog to change the settings but it didn't work. I ran **compiz --replace** then I got this error message: ```
compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 20 on window none when operation 20 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 20 on window none when operation 20 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 20 on window none when operation 20 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x560005d (OpenOffice)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect
Window manager warning: Attempt to perform window operation 26 on window none when operation 26 on none already in effect

```

Any idea on how to fix this? :)

---

### Post by wersdaluv on 2008-12-14
Just tried again with the appearance applet. It worked magically without rebooting or whatever. All I had to do was sleep. Nyahahahaha!

---

### Post by seldon77 on 2008-12-14
hmmm... from a quick look, seems like it might not be seeing your 3d graphics card. Have you tried reinstalling the restricted drivers??

---

### Post by wersdaluv on 2008-12-15
Didn't do anything. It worked when I woke up. haha

---

### Post by ellalan on 2008-12-15
Very good. Please mark the thread as solved.

---

