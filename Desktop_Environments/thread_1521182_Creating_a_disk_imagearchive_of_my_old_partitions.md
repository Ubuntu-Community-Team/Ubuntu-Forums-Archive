---
title: "Creating a disk image/archive of my old partitions"
date: 2010-06-30
forum: Desktop Environments
---

### Post by Misnomer on 2010-06-30
I am installing Linux on some spare space I left over from my previous two Windows installations.

From within Linux, what's the most risk-free way of imaging these two partitions and saving them to a single image file or archive? I want to preserve the entire partition because I have no idea what I may have forgotten to copy. What is the most suitable program that can do this?

Is there any way to run the partition in a virtual machine at a later date?

After this is done, I want to delete those old partitions and extend my Linux ones.

---

### Post by puppywhacker on 2010-06-30
Personally I would resort to commandline wizardry. There is probably fancy gui applications out there as well.

With "dd" you can do a bit-by-bit copy, in your case a partition to a file.

```
dd if=/dev/sda1 of=/partfile.img
```

The end result will be a file that you can mount as a loop device, to mount an image.

```
mount -t ext3 -o loop /partfile.img /mnt
```

You can open attach the partitions in a file from a running virtual machine like vmware, I never got windows to boot from one of those images because a vmware uses different virtual devices than the real ones, but hey this is a linux forum.

---

### Post by Misnomer on 2010-07-04
puppywhacker, cheers for your suggestion! I will be attempting this soon.

Is it possible to compress on the fly that dd command? As you can imagine it will be a big file.

I believe there are some tools that do not store empty or blank sectors on disk, drastically using file sizes of images.

I have limited space on my laptop and on the machine in question.

---

### Post by vangop on 2010-07-04
Hi! I once found this code snip on partimage site.
[http://www.partimage.org/Partimage-FAQ#What_does_partimage_give_you_over_the_following:_clear_the_free_blocks_with_DD.2C_and_copy_with_DD]("http://www.partimage.org/Partimage-FAQ#What_does_partimage_give_you_over_the_following:_clear_the_free_blocks_with_DD.2C_and_copy_with_DD")

I can't say I understand how/if it works :) but it seems to be used to save only data (not empty space) with dd.

---

