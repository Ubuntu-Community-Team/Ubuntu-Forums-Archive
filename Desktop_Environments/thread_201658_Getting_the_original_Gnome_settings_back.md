---
title: "Getting the original Gnome settings back?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by Maelgwyn on 2006-06-22
Hi guys,

I've been messing around with my Gnome panels recently and now want to put them back how they were... How do I do this?


Cheers :)

---

### Post by pauljwells on 2006-06-22
You will find in your home directory various 'dot' files (ones that begin with a ".") You can see these by selecting 'view hidden files' in the nautilus menu. These are where various programs store default settings and changes. Find anything that has 'gnome' or 'metacity' in its name and make back-up copies somewhere convenient. Then you can either root around these files to see if there's anything refering to 'gnome panels' and delete these, or just delete all of them, and then type 'killall nautilus' in a terminal (just as user, not as root) and you should get a default gnome session back.

I'm away from my machine right now, I'll post again when I'm home and have had a chance to investigate further.

---

### Post by aysiu on 2006-06-22
To make a backup copy *and* get fresh settings back, just rename the file.

For example, rename /home/maelgwyn/.gnome to /home/maelgwyn/.gnome.backup

A new /home/maelgwyn/.gnome will automatically be regenerated.

---

### Post by Maelgwyn on 2006-06-22
[quote=aysiu]To make a backup copy *and* get fresh settings back, just rename the file.

For example, rename /home/maelgwyn/.gnome to /home/maelgwyn/.gnome.backup

A new /home/maelgwyn/.gnome will automatically be regenerated.[/quote]

Thanks for that aysiu, but it didn't work =(

I deleted .gnome .gnome2 & .gnome2_private but when I log back in again (or restart) my menu bars are still in the same place and just as ugly *sigh*

I'm going to try actually deleting the files from the trashcan and then logging out & in again to see if that makes a difference...

---

### Post by aysiu on 2006-06-22
Well, unfortunately, there are quit a number of Gnome-related folders. You may want to try /home/maelgwyn/.gconf

---

