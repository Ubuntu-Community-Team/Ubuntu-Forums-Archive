---
title: "configure xfdesktop filesystem icons"
date: 2009-03-28
forum: Desktop Environments
---

### Post by fkeymo on 2009-03-28
Hey All,

Can anyone tell me how xfce decides what file system icons to put on a user's desktop by default and how I can change these defaults?
I installed xubuntu from a usb flash stick.  For some reason every user gets the following icons on their desktop:
Filesystem
Home
Trash
3GB Romovable Volume (this is a link to the / filesystem)
176MB Removable Volume (this is a link to the /boot filesystem)

I don't want the / and /boot filesystem to show up as removable media but id DO want actual removable media to show up... so i can't just un-check removable devices in the desktop properties Behaviour window.

I discovered the file ~/.config/xfce4/desktop/icons.screen0.rc 
that contains a list of the deskop icons with coordinates for where they should be placed.  I tried deleting the two unwanted entries but this has no effect and they re-appear in this file when I log back in.

What process is automatically updating this file and how can I configure it?

Thanks,
F

---

