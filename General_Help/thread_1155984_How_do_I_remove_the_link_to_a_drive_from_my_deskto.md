---
title: "How do I remove the link to a drive from my desktop?"
date: 2009-05-11
forum: General Help
---

### Post by b@sh_n3rd on 2009-05-11
Hey, I've set-up my fstab to auto-mount a drive (/dev/sdb1) at boot. The mount point is, ~/Archived. Well, Is it possible to mount the partition so that Ubuntu doesn't create a link to it on the desktop too? so that I can access the drive by going to my home dir and opening the mountpoint? Thanks for any reply...

---

### Post by coffeecat on 2009-05-11
Alt-F2 and run gconf-editor. Now: apps > nautilus > desktop. Untick 'volumes_visible'. I think that should do it.

---

### Post by b@sh_n3rd on 2009-05-11
Wow, cool...thanks dude....I owe you 1 :D

---

### Post by coffeecat on 2009-05-11
> **b@sh_n3rd said:**
> I owe you 1 :D

A pint of cold Guinness would be fine, thank you very much. :wink:

---

