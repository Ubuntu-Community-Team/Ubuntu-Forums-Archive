---
title: "Not to be dense here..."
date: 2006-07-03
forum: Desktop Environments
---

### Post by Georgie-o on 2006-07-03
but can someone tell me very specifically (maybe even in small words) how you put program launchers on the Xfce desktop?  I have the file/launcher box checked in the Desktop settings and I have folders and files visible on my desktop, but I can't seem to figure out how to put a program launcher?  I believe this is posible with this version of Xfce.  Assistance or a correction of my misconception would be appreciated.

---

### Post by rattlerviper on 2006-07-03
[QUOTE=Georgie-o]but can someone tell me very specifically (maybe even in small words) how you put program launchers on the Xfce desktop?  I have the file/launcher box checked in the Desktop settings and I have folders and files visible on my desktop, but I can't seem to figure out how to put a program launcher?  I believe this is posible with this version of Xfce.  Assistance or a correction of my misconception would be appreciated.[/QUOTE]


Choose the program you want to add launcher to the desktop to from the applications menu. Right click it, choose  add this launcher to desktop. Hope that's what your asking, if not sorry for not helping:)

---

### Post by frup on 2006-07-03
Or you can right click on the desktop and click create launcher... there you can enter in the name and the command

---

### Post by Georgie-o on 2006-07-04
Thanks for your assistance, both suggestions work under gnome, but not with Xfce.  After some further searching I found the answer in another forum and it works really easy:


The way to add Icons on the 2.6 desktop was to copy and paste.

1. Go into "/usr/share/applications", copy the *.desktop file of choice that you see there.
2. Paste the copied file in /home/YOURNAME/Desktop

Thanks again.

---

### Post by Georgie-o on 2006-07-06
one more thing...

make sure to use Thunar file manager to cut and paste icons within.  If you use nautilus it will take over your desktop and mess everything up...including getting rid of your right-click Xfce menu.   This also works great for networking to other computers on your home network.  Just copy the "network servers" link from the above noted applications folder.   You may note that doin this with Thunar makes the command:

nautilus --no-desktop network:

This is so that when ever it runs something with Nautilus in doesn't let Nautilus take over you desktop (which is problematic to undue).

---

