---
title: "It is very difficult to grab the pointer to increse/decrease an App-Window"
date: 2023-10-31
forum: Desktop Environments
---

### Post by gloster10 on 2023-10-31
uname -r
6.2.0-35-generic
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:    22.04
Codename:    jammy


I use a Laptop only with the touchpad (no additional mouse).
If I want to increase/decrease an app window, it will be very difficult to grab the pointer at the border of the app window, because the pointer does only appear for a very short time.

Is it possible to increase the time, were the pointer will be visible, or the space of the app window at the border, where the pointer stay visible ?

 I did add a picture (a mkv was my first choice, but it was not possible to upload), which pointer I have meant, please refer to the right border of Libre-Office-Calc.

---

### Post by Holger_Gehrke on 2023-11-01
Window borders on most XFCE themes are intentionally very thin because you don't need to grab the border to resize a window. Instead you're supposed to use the 'alt' key and the right mouse button for resizing. See the [documentation for xfwm4]("https://docs.xfce.org/xfce/xfwm4/getting-started").

Holger

---

### Post by #&amp;thj^% on 2023-11-01
+1 I was thinking about this last nite and now Thanks to Holger it should now be clear and easy for the resize of windows on XFCE.

---

### Post by gloster10 on 2023-11-01
@Holger_Gehrke, thank you for both, shortcut + reference.

---

### Post by bobunderwood99 on 2023-11-01
Another approach:

Right-click the title bar of the application to open a context menu that contains "Resize".

---

