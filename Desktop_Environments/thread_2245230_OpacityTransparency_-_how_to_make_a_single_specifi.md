---
title: "Opacity/Transparency - how to make a single specific application always opaque"
date: 2014-09-22
forum: Desktop Environments
---

### Post by Peter_Ring on 2014-09-22
Linux xUbuntu14 3.13.0-24-generic #47-Ubuntu SMP
This is xfwm4 version 4.11.1 (revision 2b800f4) for Xfce 4.10
Compiled against GTK+-2.24.23, using GTK+-2.24.23.

I am a fan of using the window transparency feature (i.e. window manager tweeks-> compositor), but there are some applications that don't play nicely with it. Gimp for example, pops up various windows to adjust the image attributes. Unfortunately, since the pop up has focus the parent program window becomes transparent, thus making far more difficult to adjust the image, if not impossible.


So...
1) Is there a way to make a specific  application(s) ignore the window composting feature without disabling it system wide? 
Note: the xine media player for example, ignores composting feature altogether.

2) If not, is there a way to launch an app under a different userid that has an alternate set of the session/window settings?

3) Seems to me that this problem is really a development oversight and should be addressed in future versions.  The opacity feature should respect the parent/child window relationship without making the parent translucent just because it lost focus by spawning a child.


btw - yes I am aware that you can adjust window opacity by using the ALT-mouse-wheel. However, this only allows zero opacity while the window has focus.

---

