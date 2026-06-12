---
title: "Automounting options"
date: 2008-06-16
forum: Desktop Environments
---

### Post by Krank on 2008-06-16
I just recompiled the Ubuntu Hardy kernel to incorporate the [FAT-EPOC](http://software.frodo.looijaard.name/fat-epoc/) kernel patch. I own one of those machines, see, and it'd be frightfully nice to be able to simply slot in my CF card into my card reader and be able to read stuff from it. Not to mention back stuff up. And without this patch, there's a lot of garbage in how Linux sees the file system. It's all explained in the link.

Anyways, I figured editing the card's icon properties->Volume->Settings->Mount options and add "epoc" without the quotation marks would do the same thing as adding -o epoc to the regular mount commandline.

"sudo mount /dev/disk/by-uuid/4831-884F /media/psion/secondary -t vfat -o epoc" works very well, but it's kind of clumsy.

However, if I add "epoc" to the volume's mount options in gnome, automount fails: "Invalid mount option when attempting to mount the volume "secondary", it tells me.

I'm by no means a Linux n00b, but I must admit this one stumped me. Without proper support for epoc's FAT-implementation I'm kind of useless, since I do 80% of my writing work on my Psion 5mx.

So, here's hoping for a few pointers or ideas. Please?

---

