---
title: "[SOLVED] screen resolution"
date: 2008-07-02
forum: Desktop Environments
---

### Post by evakont on 2008-07-02
i am new to ubuntu and i have a problem with my screen resolution
i have enabled the nvidia driver but i'm getting only 640x480.
i changed the values with  gksudo gedit /etc/usplash.conf but nothing happend i still have 640x480.
can i get higher resolutions like 1280x1204??

---

### Post by tsger on 2008-07-02
What do you see when you go to System/Preferences/Screen Resolution?  Can you change it there?  You might also want to install Envy, a package that installs and configures the Nvidia driver for you.  You can find it using synaptic and searching for Envy.  

By the way, what video card are you using?

---

### Post by evakont on 2008-07-02
i have nvidia GeForce 7300 Gs

---

### Post by Rhubarb on 2008-07-02
Press Alt + F2, and enter this in:
```
gksu displayconfig-gtk
```
Make sure your Graphics card drivers in there is correct, and change the Screen Model to the appropriate type.
You can adjust the resolution, video driver, and refresh rate here.
To make the changes, log out, then log back in again.

---

