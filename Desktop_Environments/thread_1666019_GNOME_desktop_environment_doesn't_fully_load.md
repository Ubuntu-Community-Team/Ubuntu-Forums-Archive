---
title: "GNOME desktop environment doesn't fully load"
date: 2011-01-13
forum: Desktop Environments
---

### Post by japcrword on 2011-01-13
My problem: The desktop environment doesn't load after I login. I can see only a gnome-terminal window with menu (but without title). If I close this terminal my login session will end.

Here's what it looks like (see attachment). 

I suspect this is connected with my upgrading GTK+ and the necessary dependencies (GdkPixbuf and glib). Here's what I did:
1. I compiled and installed glib (to /usr/local/lib).
2. I compiled and installed GdkPixbuf (to /usr/local/lib).
3. I compiled and installed GTK+ to (to /usr/local/lib).
4. I copied libgtk-x11-2.0.so.0.2200.0 (or some very similar name) to /usr/lib and changed soft link /usr/lib/libgtk-x11-2.0.so.0 to reference to it.
5. After reboot desktop didn't start at all. So I changed the link /usr/lib/libgtk-x11-2.0.so.0 back to reference to libgtk-x11-2.0.so.0.2000.0.
6. Then I could reboot and login successfully. Except that when I insert flash drive or cd it wasn't automatically mounted (as previously was). I installed gnome-volume-manager. It didn't help. When I tried to start it complained something like "failed to load libcanberra-gtk-module.so". 
7. I found this thread [http://ubuntuforums.org/showthread.php?t=1290156]("http://ubuntuforums.org/showthread.php?t=1290156") which suggested to change GTK_MODULES environment variable (to unset it). So I did - I changed it from "canberra-gtk-module" (or something similar) to an empty string. 
8. After reboot my desktop environment couldn't fully load.

Can anyone give advice to fix the issue? Thanks in advance.

---

