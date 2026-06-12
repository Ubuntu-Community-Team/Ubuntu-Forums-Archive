---
title: "DVD/CD(icon) media detection"
date: 2005-06-28
forum: Desktop Environments
---

### Post by ubuntu999 on 2005-06-28
I'm using ubuntu hoary 5.04 with Gnome

The DVD / CD icon is displayed accordingly based on the inserted media disc (DVD/CD) with my IDE DVD/RW drive that link with /dev/dvd but not my other SCSI DVD drive that link with /dev/dvd1. The icon is always displayed as CD no matter DVD/CD media inserted, is there a way to set this feature ? thanks for the help

---

### Post by doclivingston on 2005-06-28
You can't set it manually; it sound like a bug in GnomeVFS (specifically the GnomeVfsVolume part). It's probably worth reporting in Ubuntu's bugzilla, and they'll probably pass it upstream to the Gnome bugzilla.

---

### Post by ubuntu999 on 2005-06-28
Thanks for the reply, I think i'll pass this problem into bugzilla  :)

---

