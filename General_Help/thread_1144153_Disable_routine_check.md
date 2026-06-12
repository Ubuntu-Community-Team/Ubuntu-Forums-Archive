---
title: "Disable routine check?"
date: 2009-04-30
forum: General Help
---

### Post by FM1 on 2009-04-30
Fresh install of Jaunty, and I wanted some of my storage partitions to be automatically mounted, so I added them to fstab. Everything appears fine--everything mounts where it should with the correct permissions--but every time I boot, Ubuntu wants to do a routine check of them *all*. I'm used to the "routine check after 30 mounts", and that would be fine, but this is every time, every partition that it's mounting except for / and /home. How do I get it back to just every 30 mounts?

---

### Post by Polygon on 2009-04-30
hmm, this seems like a problem. I think there is some sort of config file somewhere that lets you edit how often it checks.... maybe its /etc/fstab? i dunno, try googling how to change the file system check frequency ( i have to leave now so i cannot =P )

and are you sure that there is nothing wrong with your drives? try booting up a live cd and using gparted and right click on all your partitions and "check and repair" (it might be in one of the menus rather then with a right click, i am in windows so i cannot check =P )

---

### Post by FM1 on 2009-05-04
Hm. Well, that's interesting. I looked at the file system check frequency and it seemed fine, and though I didn't actually *do* anything, I must somehow have pleased the gods of fsck because it's not checking on every boot anymore. Curious, but since copying old settings files over to my new /home has somehow given me the infamous "user's .dmrc file is being ignored..." message and it resists root's best efforts to change permissions, I'll accept the gift from the fsck gods and work on the .dmrc. :)

---

