---
title: "Can't expand partition into &quot;freed&quot; space"
date: 2009-01-07
forum: General Help
---

### Post by helwitch on 2009-01-07
So, I had 4 primary partitions on my hard drive, linux root (ext2), swap, windows (NTFS), and linux home (ext2). I decided I wanted to give linux home more space, from windows. Using qtparted, I shrunk the ntfs partition. Now I see the extra space from the windows partition, but I can't expand the linux home partition into it, the only option I have is to expand the ntfs partition back to its original size. How do I make it so the linux home partition can be expanded into the "free" space? fdisk -l and qtparted don't seem to agree on the partitioning, either. I botted to a livecd to make the changes, so it's not an issue of not being able to resize a mounted partition.

Fdisk
[IMG]http://pics.livejournal.com/heldc/pic/0007x47t[/IMG]

qtparted
[IMG]http://pics.livejournal.com/heldc/pic/0007w54b[/IMG]

---

### Post by dcstar on 2009-01-07
> **helwitch said:**
> So, I had 4 primary partitions on my hard drive, linux root (ext2), swap, windows (NTFS), and linux home (ext2). I decided I wanted to give linux home more space, from windows. Using qtparted, I shrunk the ntfs partition. Now I see the extra space from the windows partition, but I can't expand the linux home partition into it, the only option I have is to expand the ntfs partition back to its original size. How do I make it so the linux home partition can be expanded into the "free" space? fdisk -l and qtparted don't seem to agree on the partitioning, either.
.....

You can only change unmounted partitions, boot off a Live CD to do this.

---

### Post by helwitch on 2009-01-07
> **dcstar said:**
> You can only change unmounted partitions, boot off a Live CD to do this.
Sorry, should have mentioned, I booted to a live cd to make the changes. So, it's not the fact the the partition is mounted, as the partition was not mounted at the time, and I could have shrunk the partition via the software with no problem.

---

### Post by Elfy on 2009-01-07
Can you post the current output of fdisk -l please.

---

### Post by helwitch on 2009-01-07
> **forestpixie said:**
> Can you post the current output of fdisk -l please.
I did, I screenshotted it and it's in the post, as well as what qtparted shows. Are the two images not showing up?

---

### Post by Elfy on 2009-01-07
yea - there are 2 screenies - expected them to not be current.

From the two then if qparted is showing the hidden partition at the beginning are you sure there's not an extended involved somewhere - that looks like there are 5 partitions to me, if that's the case then maybe the reason you can't resize is because the extended has to be resized before a logical.

That said fdisk doesn't show that and I've not used qparted so never seen it's output.

---

