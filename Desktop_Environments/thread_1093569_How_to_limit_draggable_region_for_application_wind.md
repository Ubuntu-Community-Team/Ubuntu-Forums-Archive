---
title: "How to limit draggable region for application windows like GNOME Panel"
date: 2009-03-11
forum: Desktop Environments
---

### Post by C-- on 2009-03-11
Hi, I am developing a Java application for use in GNOME and maybe KDE that requires a persistent view at the top of the screen that a user cannot resize, move, or destroy. However, I am having issues in that a user can drag a window up behind the view, or maximize a window such that the title bar is behind this view, which means that the window's titlebar is no longer accessible and now the window cannot be moved unless the alt button is pressed.

I would like to know if there is a way to prevent users from dragging windows behind my Java application's view or maximizing a window behind the view, much like how the GNOME Panel behaves. Are there any Java functions or GNOME/Linux OS functions I can call?

---

### Post by C-- on 2009-03-17
Since I am running an X server I am assuming I need to make Xlib calls. Does anyone know Java bindings for Xlib functions that can accomplish this task?

---

