---
title: "Gparted &amp; Filesystem Properties List Different Free HD Space"
date: 2009-02-26
forum: General Help
---

### Post by insertnewsn on 2009-02-26
Hey guys,

Hopefully this is a quick and easy question to answer...

If I go into Gparted and look at my /dev/sda5/ partition, it says I have 16.59 GB of Free space.

However, if I right-click on my fileystem icon in nautilus and choose properties, it says I only have 11.3 GB of free space.

Which is correct, why do they differ, and is there something wrong here?

Also, as you can see from the Gparted screenshot, I have one extended partition (/dev/sda2) from which all other partitions (sda5, sda6, and unallocated space) emanate, but above that, there is 1.91GB of unallocated space. Without backing up everything and doing a low-level format, can I possibly add all the unallocated space to my one and only ext3 partition? (This would give me approximately 2.5 GB of space)

Any help you guys could give would be greatly appreciated!

Thanks!

---

### Post by dcstar on 2009-02-27
> **insertnewsn said:**
> Hey guys,

Hopefully this is a quick and easy question to answer...

If I go into Gparted and look at my /dev/sda5/ partition, it says I have 16.59 GB of Free space.

However, if I right-click on my fileystem icon in nautilus and choose properties, it says I only have 11.3 GB of free space.

Which is correct, why do they differ, and is there something wrong here?

Also, as you can see from the Gparted screenshot, I have one extended partition (/dev/sda2) from which all other partitions (sda5, sda6, and unallocated space) emanate, but above that, there is 1.91GB of unallocated space. Without backing up everything and doing a low-level format, can I possibly add all the unallocated space to my one and only ext3 partition? (This would give me approximately 2.5 GB of space)

Any help you guys could give would be greatly appreciated!

Thanks!

GB <> GiB.

Boot off a Live CD and you can extend the partition into the free space.

---

