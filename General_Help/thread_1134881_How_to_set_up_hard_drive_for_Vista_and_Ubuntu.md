---
title: "How to set up hard drive for Vista and Ubuntu?"
date: 2009-04-24
forum: General Help
---

### Post by Solarisphere on 2009-04-24
Is it possible to have a hard drive accessible to both Windows Vista and Ubuntu that doesn't require mounting? Or is there a way to mount an NTFS hard drive automatically at startup? Ideally I would use the ext4 or ext3 filesystem and get Vista to play nice with it. Not that that will ever happen.

At the moment I'm using the ext3 filesystem on 8.10, but I plan on doing a clean install of 9.04 and using ext4 once I decide how to repartition/rearrange the hard drives. I'm using 64bit if it makes a difference.

Note that I'm pretty new to Ubuntu, and the whole command line thing is kind of new to me. I can paste code in just fine, but I'm still don't have a very good grasp on how to work it (still haven't figured out how to use make or make-install).

---

### Post by lisati on 2009-04-24
Sounds as if you plan a setup similar to one of my laptops, which currently has a dual-boot setup of Vista Home Premium (32-bit) and Ubuntu 9.04 (64-bit, ext3, recently upgraded from 8.10).

I'm not sure how the ext4 will work, I haven't tried it on that machine yet, but have found that the Vista partition (NTFS) is easily accessible from within Ubuntu, using the "places" menu, without the need for specifically mounting it at startup. If memory serves, there are drivers available that let Windows access EXT3 volumes.

---

