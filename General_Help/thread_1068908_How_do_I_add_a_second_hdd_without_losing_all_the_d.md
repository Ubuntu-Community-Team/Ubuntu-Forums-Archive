---
title: "How do I add a second hdd without losing all the data on it?"
date: 2009-02-13
forum: General Help
---

### Post by Burnasty on 2009-02-13
I have a 320gb that I liberated from my windows computer and want to incorporate with my linux desktop.  It is filled with movies and I would really like to keep them.  Any help on how to hang on to all the data and be able to see the drive add to the drive and share over samba.  Any help is appreciated.

Brian

---

### Post by cdtech on 2009-02-13
Install the drive, use the command "sudo fdisk -l" to see which device it is. Add it to your "fstab" so that it will mount on boot.

---

