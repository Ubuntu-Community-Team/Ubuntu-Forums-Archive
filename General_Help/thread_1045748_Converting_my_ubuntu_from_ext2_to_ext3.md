---
title: "Converting my ubuntu from ext2 to ext3"
date: 2009-01-20
forum: General Help
---

### Post by dragos240 on 2009-01-20
Hey, i want to convert my ubuntu into the ext3 format, i've heard it's better. So i'd like to try it.

---

### Post by x1a4 on 2009-01-20
Hi,
Use a partition tool like gParted and reformat the partition in question with the ext3 filesystem.  Remember that you will lose all data on that partition so do a backup first.

---

### Post by JakeWatkins on 2009-01-20
I'm not sure about all of that.. but if you want to do it on the partition you're on... you'll have to use a Live CD first.

Gparted comes with Ubuntu.. so that's not a problem.

But I would do a back up of everything anytime you're messing with your HDD. ;- )

---

### Post by jerome1232 on 2009-01-20
Wow, you don't have to reformat the drive!!!

ext3 is just ext2 with a journal, you can use tune2fs to slap a journal on an ext2 filesystem, thus making it ext3.

Here's a quick how to about it, check out 'man tune2fs' for detailed info on the tune2fs program.

[http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm)

It involves unmounting the filesystem so you will probably need a live cd, and of course keep your backups up to date, just in case something goes horribly wrong.

---

### Post by JakeWatkins on 2009-01-20
Doesn't Ext3 give performance upgrades from Ext2?

I know Ext4 will give crazy performance upgrades from Ext4.

= D

---

### Post by jerome1232 on 2009-01-20
Actually I believe having a journal makes it slower than ext2, the benefit of ext3 is fsck's go MUCH faster and it's more reliable.

---

### Post by dcstar on 2009-01-20
> **JakeWatkins said:**
> Doesn't Ext3 give performance upgrades from Ext2?

I know Ext4 will give crazy performance upgrades from Ext4.

= D

EXT3 is EXT2 with journaling - which imposes overheads but makes your files more resilient to power outages etc. on "normal" hard drives. If you care about you data then you will use a journaling filesystem.

You don't use journaling on solid state filesystems (USB sticks etc.) because the extra writes reduce the life of these things, and there isn't any benefit as with a mechanical drive.

---

