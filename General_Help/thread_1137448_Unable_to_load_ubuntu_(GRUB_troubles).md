---
title: "Unable to load ubuntu (GRUB troubles)"
date: 2009-04-25
forum: General Help
---

### Post by VON_CAPO on 2009-04-25
Hi, my desktop has 3 hard drives, 2 sata and 1 ide.

The first sata contains a XP partition and a ext4 for Ubuntu.
The second sata and the ide one are for storage. 

It always happens that the ubuntu installs GRUB in the ide drive (I think this is the case again).

Before I solved this unplugging the ide one and reinstalling Ubuntu, in that case GRUB was installed into the right drive (the first sata).

This time I am unable to open the desktop because it is encased in a tight and huge furniture and I should dismantle it to reach the computer.

How can I move GRUB to the right drive?

---

### Post by logos34 on 2009-04-25
see link in my signature below to restore grub.

For 'setup' step use whatever the / is (what 'find' shows).

Then make sure the bios is set to boot first sata

---

### Post by VON_CAPO on 2009-04-26
> **logos34 said:**
> see link in my signature below to restore grub.

For 'setup' step use whatever the / is (what 'find' shows).

Then make sure the bios is set to boot first sata

Fixed. Thank you so much.

---

