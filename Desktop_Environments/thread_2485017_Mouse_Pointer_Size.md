---
title: "Mouse Pointer Size"
date: 2023-03-17
forum: Desktop Environments
---

### Post by pfanwick on 2023-03-17
I am having problems with the size of the mouse pointer when not in an application.  I am running Ubuntu 22.04.  I just installed a GeForce 1080 graphics card and am using the recommended Nvidia 525 driver.  The screen resolution is 3840x2160 with a scaling factor of 200% ad HiDPI on .  This is sent in MATE.  However, I checked in GNOME and UBUNTU and both have the same problem.  Changing the size of the cursor  in MATE Appearance does make the cursor bigger in FIREFOX, terminals and other applications but does not affect the size of the cursor on the desktop.  I have tried the recommended changes from web searches but none have had any effect.  The very small cursor is hard to find and I would like a way to make it bigger. I am sure this is because of the HiDPI scaling as when I turn it off the pointer is the same between apps and the desktop.  Thanks for any help.

---

### Post by Apanta on 2023-04-06
Hy
Assuming you're using gnome, install dconf-editor and then follow the path: org/gnome/desktop/interface. Double click on interface, scroll to Palette custom value and change the number. Increase the default value to 32 or more . Attention the size increases every 4 - 6 numbers.

---

