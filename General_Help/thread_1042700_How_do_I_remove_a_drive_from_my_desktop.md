---
title: "How do I remove a drive from my desktop"
date: 2009-01-17
forum: General Help
---

### Post by Baasha on 2009-01-17
I have a small partition on my drive that is formatted in Fat32 to support some files that are used in my dual boot (Ubuntu/Windows) system.  This partition shows up on my desktop as "8 GB Media".  I don't want it cluttering up my desktop as I can easily access it by other means when I need it.  Is there a way to take it off the desktop without unmounting it?

---

### Post by fenian on 2009-01-17
Open a termianl and enter...

> gconf-editor

Click the triangle next to apps
Scroll down to Nautilus and click the triangle
Click on desktop
In the window uncheck volumes_visible

This will cause all volume icons to not be displayed on the Desktop,so if you put in a cd the icon won't appear on the desktop bt will be accessible from the Places menu.

---

### Post by Baasha on 2009-01-18
Thanks Fenian, but that leaves me wondering why other partitions don't also show up on the desktop?  For instance, I also have two other drives, Windows1 and Windows2, that hold my Windows OS, but they don't show up.  I conclude from that, that it isn't just the different formatting that makes Linux pick out which drives to put on the desktop.  It would be nice if I could still have plug in devices like a cd or a memory card from my camera show up on the desktop, but maybe I am expecting too much.

---

### Post by mcduck on 2009-01-18
If you do what fenian suggested it will disable _all_ mounted drives on the desktop.

If you just want to remove that one drive/partition from desktop, (but still wish to keep it mounted) you should edit /etc/fstab to mount it anywhere else than in /media. /mnt would be a good choice.

---

