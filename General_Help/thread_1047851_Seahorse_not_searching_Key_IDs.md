---
title: "Seahorse not searching Key IDs"
date: 2009-01-22
forum: General Help
---

### Post by ookooboontoo on 2009-01-22
Hi,

I am using Hardy and when using the passwords and encryption keys program(Seahorse), I cannot seem to search for a user when I enter a Key ID, does this happen to others? And there is always a progress bar that never changes, whether searching or not.

I can search on a name but not key IDs

A

---

### Post by ookooboontoo on 2009-01-22
> **ookooboontoo said:**
> Hi,

I am using Hardy and when using the passwords and encryption keys program(Seahorse), I cannot seem to search for a user when I enter a Key ID, does this happen to others? And there is always a progress bar that never changes, whether searching or not.

I can search on a name but not key IDs

A

Having spoken to Adam Schreiber this may be part of a bug that was thought to be fixed. I will update here if I hear more but it would be good if others can confirm or deny its existence
> 
Try searching 0x7108E308 instead.  I thought someone had contributed a
fix that appended a 0x onto keyids that were searched for, but I'm
experiencing the same bug in TRUNK.I did this but still no joy.

A

---

### Post by ookooboontoo on 2009-01-23
My thanks to Adam, who has filed the bug report;
[http://bugzilla.gnome.org/show_bug.cgi?id=568799](http://bugzilla.gnome.org/show_bug.cgi?id=568799)
He knows the best route for this and look forward for this to be resolved in time.

Cheers :)

A

---

