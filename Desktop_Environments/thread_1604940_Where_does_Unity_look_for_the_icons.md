---
title: "Where does Unity look for the icons?"
date: 2010-10-24
forum: Desktop Environments
---

### Post by fladd on 2010-10-24
Hi there,

on my UNE 10.10, one application (Renoise) does not have an icon in Unity, but a standard application icon, unless I start the application, then the standard icon turns into the Renoise icon.
So, I was wondering, where does Unity try to read the icon from? I have the Renoise icon in /usr/share/icons, but that does not help.

Regards,
fladd

---

### Post by ankspo71 on 2010-10-25
Hi,
Most icons are located in /usr/share/icons and /usr/share/pixmaps.

As far as where it is looking for the icon, I think that would only depend on the shortcut that was created for Renoise. Do a search for a file called renoise.desktop (*.desktop files are shortcuts) and read the file with a text editor to see if is looking for the icon in a special location. It might say the icon is located in an unusual directory and/or not part of your currently selected icon theme set. 

The renoise icon might have something different about it too, such as a different size or filetype causing it to not get displayed initially.

Hope this helps.

---

