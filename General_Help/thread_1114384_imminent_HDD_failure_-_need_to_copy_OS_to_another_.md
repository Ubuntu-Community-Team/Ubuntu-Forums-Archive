---
title: "imminent HDD failure - need to copy OS to another disk"
date: 2009-04-02
forum: General Help
---

### Post by 3pinner on 2009-04-02
I have a SATA drive that doesn't want to spin up right away. Sometimes it takes several boots to get it going. connections are OK, so I'm suspicious of the drive itself.

If I unstall the same version of  UBuntu on another drive, what is the best way to copy my  /home folder to the new drive and restore all the connections?

Thanks!

---

### Post by dcstar on 2009-04-02
> **3pinner said:**
> I have a SATA drive that doesn't want to spin up right away. Sometimes it takes several boots to get it going. connections are OK, so I'm suspicious of the drive itself.

If I unstall the same version of  UBuntu on another drive, what is the best way to copy my  /home folder to the new drive and restore all the connections?

Thanks!

Just use gparted to copy each of the partitions and then reinstall grub (search out the detailed instructions).

---

