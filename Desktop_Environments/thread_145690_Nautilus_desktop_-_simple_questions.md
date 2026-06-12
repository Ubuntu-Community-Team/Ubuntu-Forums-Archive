---
title: "Nautilus desktop - simple questions"
date: 2006-03-16
forum: Desktop Environments
---

### Post by FIONEX on 2006-03-16
Hey,

I'm having issues with my nautilus desktop.  There's icons on there that I don't want like the windows partitions and my FTP connections.  However, if I delete them off the desktop, they are unmounted.  Also, I created a launcher "nautilus computer:///" which simulates "My Computer" from windows, which I find to be much more efficient to access the system files.  I want this launcher to be in the top left part of the screen even if I click "clean up by name".  How would I go about doing that?

---

### Post by Zelut on 2006-03-16
As far as removing mounted drives from your desktop without unmounting them you can do this with the gconf-editor.  ALT-F2 to open the editor, find Apps > Nautilus > Desktop and you should be able to activate/de-activate displaying volumes (CD/DVD/mounts), my computer icon, home icon, etc.  Is that what you're looking for?

As far as locking an icon to a certain position, I dont know.  Sorry.

---

### Post by akiro.yamamoto on 2006-03-17
Go to :
Applications >> System Tools >> Configuration Editor.
When the Configuration Editor appears click on:
apps >> nautilus >> Desktop 
You can have the mounted drives and Cd-rom appear or not, as required.
As well as specify if the Computer (same as the Win version) is visble etc.
See the screenshot.
Hope this helps ;)

---

### Post by irw on 2006-03-17
That gives you all or nothing with mounted drives - all HD partitions and CD/DVD/USB devices.

Is there any way to specify not to show hard disk partions, but to show all USB / Cds etc that have been automounted?

I have the mount point for my hard disk partitions in/mnt andt all removable media in /media - can this be used to differentiate?

---

