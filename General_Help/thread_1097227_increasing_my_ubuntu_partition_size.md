---
title: "increasing my ubuntu partition size"
date: 2009-03-15
forum: General Help
---

### Post by Jameshardy88 on 2009-03-15
Hi i want to make my ubuntu partition size smaller taking space that i have freed on my windows partition. I have been trying to use gparted, i know how to shrink my windows partition so that it becomes unallocated, but how do i then add that space to my ubuntu partition?

thanks for the help,

James

---

### Post by mrsteveman1 on 2009-03-15
You can use the gparted livecd, or whatever we're using instead these days, the Ubuntu livecd can probably do it too since it has gparted on it.

You could probably get away with resizing the filesystem while its in use, but you're supposed to use LVM for that sort of thing since the partition actually needs to be resized first. 

Give the ubuntu livecd a try first :)

---

### Post by Jameshardy88 on 2009-03-15
Thats what i have been using i can make it so that i have unallocated space form my windows partition but i don't know how to add that space onto my ubuntu partition.

---

### Post by 73ckn797 on 2009-03-15
In gparted can't you completely delete the freed space to an unallocated space (no partition and not formatted) then just expand the Linux partition over that? It sounds like what you have, the unallocated section, but have not expanded the Linux into that. I assume you have used the arrows on the end of the partiton graphic to move the size.

---

### Post by Jameshardy88 on 2009-03-15
ive got it so that ive got some of my windows partition shaved off into unallocated space but i can't then add that space into my ubuntu partition, i don't seem to have any arrows to re-size (i remember there being some when i installed it originally though) and i cant delete the unallocated space.

---

### Post by mrsteveman1 on 2009-03-15
If Windows was at the beginning and Ubuntu was at the end of the drive you will have to move the Ubuntu partition and not just resize it.

There is an option to move partitions in gparted, i've done exactly what you are trying to do before. Move it so the free space is at the end of the drive, then you can resize it easily.

---

### Post by Jameshardy88 on 2009-03-15
is it ok to move my windows partition behind the ubuntu one then? will this not interfere with any of the boot loading menus or anything?

---

### Post by 73ckn797 on 2009-03-15
If the unallocated partition is at the front side of Windows then you cannot move or increase Linux to that. You would have to first resize Windows to the front/left side (as graphically viewed) then decrease it on the back end just before the Linux partition. You then could resize Linux into that unallocated area you created. Do this from the LiveCD.

---

### Post by mrsteveman1 on 2009-03-15
Be careful moving windows, while you can resize it pretty easily, if you actually move it, Windows sometimes (all the time?) refuses to boot, and requires you manually redo the bootloader with the windows cd.

---

### Post by Jameshardy88 on 2009-03-16
thanks for all the help guys, i have now successfully re-partitioned my hard drive =)

---

### Post by 73ckn797 on 2009-03-16
Good deal.

---

