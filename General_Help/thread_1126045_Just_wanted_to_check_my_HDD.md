---
title: "Just wanted to check my HDD"
date: 2009-04-15
forum: General Help
---

### Post by gibxam on 2009-04-15
Hello,

I've tried to set up my first dual boot. I started by un-installing everything and then getting BT3 installed on a very small section on my HDD then I re-installed Ubuntu on the rest of it. I'll be honest I'm not really sure if I did everything right but I can now boot into either BT3 or Ubuntu so I know thats at least working however I'm not sure if I'm utilizing my HDD to its full use. This is what my fdisk -l looks like, I'm just look for a little bit of re-assurence to make sure I did everything right :). This whole experience really made me realize how much I still have to learn about Linux and free myself from the MS cult ;) your help is appreciated.

Max

```

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         925     7430031   83  Linux
/dev/sda2             926        1053     1028160   82  Linux swap / Solaris
/dev/sda3            1054        9726    69665872+   5  Extended
/dev/sda5            1054        9367    66782173+  83  Linux
/dev/sda6            9368        9726     2883636   82  Linux swap / Solaris

Disk /dev/sdb: 2013 MB, 2013265920 bytes
16 heads, 15 sectors/track, 16384 cylinders
Units = cylinders of 240 * 512 = 122880 bytes
Disk identifier: 0x7df0832e

```

---

### Post by Tipped OuT on 2009-04-15
Hmm..you could just do it the easy way and install windows and use Magic Partitioner. :p

---

### Post by Chesamo on 2009-04-15
See how the first Start cylinder is 1, and the last End cylinder is 9726? That means all your space is utilized.

HOWEVER! You only need one swap space on a drive. You don't need one per distribution.

---

### Post by gibxam on 2009-04-16
Chesamo,

Do you know how I could fix this? Does it really even matter since the swaps are pretty small? I'll be honest I'm pretty terrified of messing with the the partitions after this whole ordeal ;)

---

### Post by Chesamo on 2009-04-16
Since your swaps are in different places (not next to each other), I'd just leave them. If you're feeling brave, you can boot into a LiveCD (RIPLinuX is great for this) and delete the two swaps, move the second data partition over, and create a swap at the space in the empty space at the end.

You don't need to, though. It just seems like a waste of space.

---

