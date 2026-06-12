---
title: "Desktop Icons became large"
date: 2014-05-14
forum: Desktop Environments
---

### Post by RyeMan on 2014-05-14
I was doing some work with files (just picture files in PCmanFM) and when I was finished my desktop Icons became very large and I haven't been able to reduce them.  I tried Monitor and desktop settings but see no options.  My screen resolution hasn't changed either.  Any ideas would be greatly appreciated.

-Computer-
Processor        : 2x Intel(R) Pentium(R) 4 CPU 3.00GHz
Memory        : 2575MB (445MB used)
Operating System        : Ubuntu 14.04 LTS
Date/Time        : Wed 14 May 2014 07:22:21 AM MDT
-Display-
Resolution        : 1366x768 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation

---

### Post by Dennis N on 2014-05-14
When viewing a folder in PCManFM with the folder view mode set to Icon View, whenever you zoom in and out the Desktop icons will enlarge or shrink along with the those in the window you are viewing. If you use thumbnail, compact, or detailed view mode, they do not.

So to fix this, set PCManFM to icon view mode, zoom out to the size you like. Then switch to another view mode.

---

### Post by RyeMan on 2014-05-14
Thanks, but it only changes the icons while in the file manager, the desktop icons stayed the same.

---

### Post by Dennis N on 2014-05-14
> **RyeMan said:**
> Thanks, but it only changes the icons while in the file manager, the desktop icons stayed the same.

The desktop icons will change (along with all icons in the file manager window) only if you open the file manager, set it to Icon View, and then Zoom in or Zoom out. If you don't have the file manager open and the active window (what folder is open doesn't matter), the desktop Icons will not change with zoom in or zoom out (CTRL+ or CTRL-). I just checked this again on two Lubuntu 14.04 installations just to make sure this is the way it works. I could be wrong, but I don't think you can change the desktop icon size independently of the icon size in the file manager. They are linked.

---

### Post by RyeMan on 2014-05-15
It worked!!!  Thanks so much Dennis.[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

---

