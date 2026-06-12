---
title: "how can i change boot drive"
date: 2009-02-21
forum: General Help
---

### Post by vbdanl on 2009-02-21
i know this is weird, but not sure how to change it.
i have a system with 2 hd.
hd0 has puppy on it and is only 2.2g
hd1 has ubuntu on it and has 8.1g

i want to copy (with dd or gparted) these partitions to a different drive (probably 20 or 40G).  i can only have cables for 2 drives, so i need to be able to boot from one drive, and copy its contents to the "new" larger drive (its not really new, but you know what i mean).

right now i don't seem to be able to remove either drive and boot.
if i remove the 2nd drive, and try to boot just using the first drive, i get a grub error.

if i remove the 1st drive, and try to boot just using the second drive, i get a "system disk error" or some such error message.

thanks in advance for your help..

---

### Post by oiad on 2009-02-22
You can just use a live cd, then nothing needs to be mounted.  If you feel comfortable in ubuntu then use it, or you could use something like knoppix.  Just boot into the live cd and use dd to copy the first drive onto the new drive, then shutdown switch the cables and reboot the live cd and copy the other drive.

---

### Post by vbdanl on 2009-02-22
> **oiad said:**
> You can just use a live cd, then nothing needs to be mounted.  If you feel comfortable in ubuntu then use it, or you could use something like knoppix.  Just boot into the live cd and use dd to copy the first drive onto the new drive, then shutdown switch the cables and reboot the live cd and copy the other drive.

thanks.  i ended up mounting these drives as secondary on another system, then used dd to copy off the partitions.

---

