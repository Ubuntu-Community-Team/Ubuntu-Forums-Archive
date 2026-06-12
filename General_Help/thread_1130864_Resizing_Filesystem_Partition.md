---
title: "Resizing Filesystem Partition"
date: 2009-04-20
forum: General Help
---

### Post by Flexico on 2009-04-20
Here is my hard drive partition list:

[COLOR="Green"][---fat32---][/COLOR][COLOR="DimGray"][--unallocated--][/COLOR][COLOR="DarkOrange"][---ubuntu---][/COLOR][COLOR="Indigo"][-swap-][/COLOR]

I just resized the [COLOR="green"]fat32 storage partition[/COLOR] (not running windows from that) to make the [COLOR="DimGray"]unallocated space[/COLOR] to expand the [COLOR="DarkOrange"]ubuntu partition[/COLOR] onto (because I'm running low on space) but when I try to resize the [COLOR="DarkOrange"]ext3 partition[/COLOR] (booting from startup disk of course because you can't edit a partition while booting from it) it won't let me move it "left" in the filesystem, it only lets me adjust the size on the "right" side.

How do I do that?

---

### Post by James_Lochhead on 2009-04-20
Hmm very strange. Make sure the partition is not mounted. You are using grub on the Live CD right?

---

### Post by Flexico on 2009-04-20
I made a USB startup disk from the Live CD and that's what I'm using. The partition is not mounted.

I'm going to try to find another partitioning program to see if that will work. :)

---

### Post by Flexico on 2009-04-20
Um, scratch that. There are none, at least that came up in Add/Remove Apps.

Also, the fat32 partition is gone now. I want to expand Ubuntu to the whole drive.

---

