---
title: "[SOLVED] Removing Linux"
date: 2008-12-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bengreer on 2008-12-31
I am currently removing linux using the live cd. I have these partitions: fat32, linux-swap, ntfs, ext 3.  It is dual booted with windows!

Which partitions should i remove, resize, etc.

Your help would be much appreciated!

---

### Post by ArKay on 2008-12-31
> **bengreer said:**
> I am currently removing linux using the live cd. I have these partitions: fat32, linux-swap, ntfs, ext 3.  It is dual booted with windows!

Which partitions should i remove, resize, etc.

Your help would be much appreciated!
linux-swap and ext3 should be the guys to go. 

Doing so should put you back to a single install of windows without Grub asking you where to boot to.
I _think_ the fat32 is your windows page file (might be wrong)
ntfs should be your windows installation


You might want to wait for someone to confirm it in case I'm wrong though...

---

