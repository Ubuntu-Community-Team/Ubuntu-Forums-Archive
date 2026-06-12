---
title: "disk copy tool?"
date: 2009-02-28
forum: General Help
---

### Post by zuheyr on 2009-02-28
Hello,

I installed a new hard disk. I would like to make an exact copy of my first hard disk that holds vista and Ubuntu (thus ntfs and ext3 systems).

Is there a linux tool that will allow me to make an exact copy of the first hard disk so that I can replace it with a larger capacity disk and boot from the copied disk?

Many thanks for reading, best regards, Zuheyr

---

### Post by justleen on 2009-02-28
you can use dd, to make bit-for-bit copy of a disk.
Or use plain old cp. yet another option would be to use rsync.

---

### Post by zuheyr on 2009-03-01
Hi! Thank you.

Yes I did some search in the Ubuntu forums but what seems to me very unclear is whether do I have to partition the target disk first with, say, gparted, or is there a tool that could also create the identical partitioning?

I saw that people had to edit fstab files etcc and I simply do not have enough knowledge to do that yet.

Rsync command also seemed very complicated with a large amount of options to choose from.

But this seems to be the right time to learn and master these.

Thank you for your help, best regards, Zuheyr

---

### Post by vanadium on 2009-03-01
What you want requires some technical level, indeed. It is much easier to reinstall the system. The added benefit is that you have a new, updated and clean system.

First make sure your backup of your personal files is up to data. After the reinstall, just place your data back.

---

### Post by Xiong Chiamiov on 2009-03-01
I've used [partimage](http://www.partimage.org/Main_Page) a few times to copy partitions around.  It works pretty well, and you can either use their live cd, or boot onto your Ubuntu CD and install it there.

---

### Post by woosey on 2009-03-01
Hi,

Its possible to copy the disk structure from one disk to another -
```

sfdisk -d /dev/*orignal disk* | sfdisk /dev/*new disk*

```

I would then mount a live cd / usb pen and rsync all your files across.

---

