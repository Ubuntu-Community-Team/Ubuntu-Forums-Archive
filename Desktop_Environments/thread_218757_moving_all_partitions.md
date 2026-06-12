---
title: "moving all partitions"
date: 2006-07-19
forum: Desktop Environments
---

### Post by Jhongy on 2006-07-19
Due to this new-found Linux obsession, I have just got a new 250 gig hard disk... I've scribbled away on the back of an envelope, and have come up with a fantastic new partitioning solution.... BUT... 

THis will involve copying over all the contents from existing partitions onto the new drive. Including / and  /boot.

The plan is to install the disk, set up the partitions.... which I can probably manage myself. But then how do I transfer stuff over?

I was thinking I could boot up  with the live CD, mount the existing / as, say, /old (should it be /media/old or something?), then mount the new / as /new, and then copy stuff over. Then do the same for the other partitions (apart from /boot). Then update the GRUB config file. 

**Then what?** How do I ensure that the partitions mount in the right places when I boot without the Live CD? Do I need to edit another file somewhere?

Then, the final task will be moving the /boot partition. I assume I'll be able to do that relatively easily, marking the new partition as bootable from within Linux? I assume I also need to update GRUB again to reflect this?

FINALLY---- when I plug in the new disk, is there any chance it will suddenly become device hda, shifting the others to hdb and hdc, throwing the bootloader into a hissy fit and rendering me unable to do anything? Just a thoguht.

Thanks in advance for helping a lowly noob out.

---

### Post by aysiu on 2006-07-19
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) may help you, but you'll still have to edit your /boot/grub/menu.lst and /etc/fstab files.

---

### Post by Jhongy on 2006-07-19
Ahhh, excellent, thank you. /etc/fstab looks like the piece of understanding I was missing.

---

### Post by Jhongy on 2006-07-19
One more question.. that article you linked to talks about using PartImage to create an image file.

Which program would be best to copy all files from one partition to another, preserving everything? Something equivalent to the old MS-DOS xcopy command?

---

### Post by Ramses de Norre on 2006-07-19
This command will take care of links and stuff to:
```
cd old_part
find . -depth -print0 | cpio --null --sparse -pvd new_part
```
Just cd to the partition containing the data and change "new_part" to the path to the mountpoint of the new partition. And if it's the same kind of drive your device nodes for your drives (the /dev/ stuff) shouldn't change, make sure the jumpers are set the same when it are IDE drives.

Ow and for what it's worth: I always use knoppix for this things and I think it works far better as the ubuntu live cd, knoppix is made with this kind of things in mind.

---

### Post by Jhongy on 2006-07-19
Thank you. I notice that, once copied, all the files have had their "date created" timestamps reset to today....

Does this matter, and/or is there a better way to copy them over?

---

