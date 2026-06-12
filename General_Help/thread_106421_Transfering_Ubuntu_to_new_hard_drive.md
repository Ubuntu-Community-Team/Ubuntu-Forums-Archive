---
title: "Transfering Ubuntu to new hard drive"
date: 2005-12-20
forum: General Help
---

### Post by bulio on 2005-12-20
Hi everyone,

Currently, I use an 8.4 GB hard drive for ubuntu, and soon I will be buying a 120GB Hard drive. Since my computer has only 1 hard drive bay, I want to transfer my current ubuntu install over to the new hard drive. (I have enough cables (IDE etc.) to connect the HD to the PC, just can't put the HD into a drive bay) So how would I move my install to the new hard drive?

Thanks

---

### Post by az on 2005-12-20
Use parted.

You can run parted, create whatever partitions you want o the new drive, copy the data from your current partition over to the new disk, and then resize the filesystem on the partition to the maximum (the filesyste will still be the same size as it was on the old disk).  Then,  mount it and then chroot into it and run 

sudo grub-install /dev/hdb (it will actually be hda, but it does not know that)

Then shut down and put the drive into position and boot into it.

---

### Post by thespazzz on 2005-12-20
I use Norton Ghost to clone drives when I do this sort of thing.  Hasn't failed me yet.  Connect both drives *You don't have to actualy mount the drive in physical computer just connect it to the slave spot on your IDE cable and put a power chord in.  Ghost the Master drive to the slave drive then just swap the drives.

---

### Post by austin on 2005-12-22
What is to be done, if the the ide port changes for the transfer (copying the system from /dev/hdb1 to /dev/hda1 e. g.)?

I did it changing menulst and fstab. First I realized, that the graphical boot screen vanished on "loading modules" and the rest went text-based. Didn't care because the system worked fine, but this showed me that my transfer was not 100%. Later (many sessions later) the transferred system got broken (fatal boot error "module minix not found"), but maybe this is not related to the transfer.

---

### Post by Mr. Electric Wizard on 2005-12-22
I believe there is a Knoppix tool to copy an image of your current hard drive, allowing you to copy this image to another computer on your network.
Then after installing the new hard drive, you can use Knoppix again and copy the image back to the new hard drive...

---

