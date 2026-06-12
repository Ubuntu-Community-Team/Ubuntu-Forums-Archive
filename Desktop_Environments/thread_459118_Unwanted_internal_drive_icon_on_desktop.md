---
title: "Unwanted internal drive icon on desktop"
date: 2007-05-30
forum: Desktop Environments
---

### Post by QwUo173Hy on 2007-05-30
I've edited fstab to include a second harddrive. But Gnome puts the icon for the drive on the desktop. I can access the drive from the places menu so I really don't want the icon there.

How can I get rid of it? It won't let me delete it. It says I "cannot remove volume "disk" to trash" and that if I want to unmount it, I should use the context menu.

---

### Post by bapoumba on 2007-05-30
Anything mounted in /media will show up on your desktop, provided that > Apps > Nautilus > Desktop > volume_visible key in gconf-editor is ticked.

So you have 2 solutions:
1- untick the key, but other mounted volumes (like CDroms, DVD, usb drives and such) will no longer show up on your desktop
2- mount your drive in another file than /media, in /mnt for ex

---

### Post by QwUo173Hy on 2007-05-30
Thank you bapoumba, that is a very thorough answer!

I'll go for option No. 2.

---

