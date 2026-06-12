---
title: "cifs volumes and the places menu"
date: 2010-06-11
forum: Desktop Environments
---

### Post by nerdzero on 2010-06-11
I'm hoping someone can guide me to some sort of solution here as I've been searching for a while now.

I've got my Documents, Music, Pictures, and Videos folders pointing to shares on my server via CIFS volumes mounted in my fstab file.  The problem is I end up with duplicate entries in the Places menu.

I can remove the bookmarks for those folders but then the menu looks ugly and while I can reassign the icon for the volumes in nautilus by browsing to computer:///, it doesn't seem to update the icons for the volumes in the Places menu.

Does anyone have any suggestions to try?  I've circled the offending menu entries in the attached screenshot.

---

### Post by nerdzero on 2010-06-21
bump

---

### Post by nerdzero on 2010-07-01
bump

How about an alternative to CIFS volumes?  Can I get the same functionality with another approach?

---

### Post by nerdzero on 2011-03-24
In case anyone ever runs into this, here is the solution: [http://askubuntu.com/questions/16904/how-do-i-hide-cifs-volumes-in-the-places-menu](http://askubuntu.com/questions/16904/how-do-i-hide-cifs-volumes-in-the-places-menu)

Basically mount then in /mnt and then replace the folders in your /home folder with symbolic links.

---

