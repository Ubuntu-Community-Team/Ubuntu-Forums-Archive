---
title: "Space reserved for root on LVM - How do I change it?"
date: 2009-03-26
forum: General Help
---

### Post by OttifantSir on 2009-03-26
I have three 1TB discs formatted with ext3 in LVM mounted as ~/share
Problem is, before I set up LVM I didn't remember to change the space reserved for root on these discs, and 5% of 3TB is quite a lot of space to waste where it's not needed. I have a 250GB disc that I use for root and /home where the space reserved is tuned accurately.

I just want to know if I need to use LVM-commands to change this, or if it's enough to use tune2fs.

If I need to use LVM-commands, which one(s) is it?

---

