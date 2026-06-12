---
title: "How to make an XP partition for games from ubuntu?"
date: 2009-01-11
forum: General Help
---

### Post by nintennuendo on 2009-01-11
I installed ubuntu on the whole hard drive, all 60gb of it, on my laptop. The only computer I have or use, so whatever. What is the preferred method to create an 8 or so gigabyte partition for microXP and a couple games. and yes, that will be enough. I don't think making one in gparted or such would boot from it, since theres no info, so i have to edit something, right?

---

### Post by chex_m8 on 2009-01-11
You can't partition from ubuntu, you need a livecd or gparted.

---

### Post by jocko on 2009-01-11
> **chex_m8 said:**
> You can't partition from ubuntu, you need a livecd or gparted.
Of course you can partition from ubuntu. Just install gparted.
But you can't make changes to mounted partitions, so if you need to resize the partition you have ubuntu installed on, you will have to do it from a live cd...

---

### Post by nintennuendo on 2009-01-11
> **jocko said:**
> Of course you can partition from ubuntu. Just install gparted.
But you can't make changes to mounted partitions, so if you need to resize the partition you have ubuntu installed on, you will have to do it from a live cd...

alright, so, if i do that, then what?  just install microxp onto this 6gb or so and it'll boot with grub?  or will it overwrite?  not be recognized?

---

### Post by jocko on 2009-01-11
> **nintennuendo said:**
> alright, so, if i do that, then what?  just install microxp onto this 6gb or so and it'll boot with grub?  or will it overwrite?  not be recognized?

Windows will unfortunately overwrite the mbr, where the first part of grub is installed.
But don't worry, this can be fixed. Just make sure you have a bootable ubuntu live cd before you start. Check out [this page]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") for instructions for how to restore grub after a windows install.

---

### Post by nintennuendo on 2009-01-11
> **jocko said:**
> Windows will unfortunately overwrite the mbr, where the first part of grub is installed.
But don't worry, this can be fixed. Just make sure you have a bootable ubuntu live cd before you start. Check out [this page]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") for instructions for how to restore grub after a windows install.

I think i'm going to go with this method:  [http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

Thanks!

---

