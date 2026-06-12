---
title: "change partitions for more Ubuntu room"
date: 2006-01-12
forum: General Help
---

### Post by DaveRowell on 2006-01-12
Seems that Ubuntu is a pretty good place to live - I like it - I want it to be the primary OS on my box.

My 150 GB drive is partitioned
   1 - 4.4 GB fat32 Compaq's &^*#*(@! software partition (XP's D:\)
   2 - 130 GB ntfs Windoze XP (XP's C:\) - about 9 GB accessably free
   3 - 13.6 Lunux / - about 7 GB free
   4 - entry for extended partitions
        5 - 0.6 GB Linux swap

I need to keep Compaq's boat anchor and some XP but want to move a bunch of files, basically My Documents, onto a FAT32 partition so that both systems can read and write the common files.  I can dump them to DVD's and reload 'em from there so I don't have to be able to make a simple file copy.

I THINK I'd also like to have /home, /usr and /var on another partition.  This make sense so far?

Maybe make the new partition table look like this?  Suggestions??
1 - 4.4 GB Compaq
2 - 90 GB Windoze
3 - 30 GB new FAT32 common files
4 -
   5 - 7 GB new Ubuntu /
   6 - 18 GB new /home, /usr & /var
   7 - 0.6 GB new Ubuntu swap

Can I pull this off without reinstalling Ubuntu?  How???  Or should I wait for Dapper Drake and start all over?

---

### Post by neoflight on 2006-01-12
[QUOTE=DaveRowell]Seems that Ubuntu is a pretty good place to live - I like it - I want it to be the primary OS on my box.

My 150 GB drive is partitioned
   1 - 4.4 GB fat32 Compaq's &^*#*(@! software partition (XP's D:\)
   2 - 130 GB ntfs Windoze XP (XP's C:\) - about 9 GB accessably free
   3 - 13.6 Lunux / - about 7 GB free
   4 - entry for extended partitions
        5 - 0.6 GB Linux swap

I need to keep Compaq's boat anchor and some XP but want to move a bunch of files, basically My Documents, onto a FAT32 partition so that both systems can read and write the common files.  I can dump them to DVD's and reload 'em from there so I don't have to be able to make a simple file copy.

I THINK I'd also like to have /home, /usr and /var on another partition.  This make sense so far?

Maybe make the new partition table look like this?  Suggestions??
1 - 4.4 GB Compaq
2 - 90 GB Windoze
3 - 30 GB new FAT32 common files
4 -
   5 - 7 GB new Ubuntu /
   6 - 18 GB new /home, /usr & /var
   7 - 0.6 GB new Ubuntu swap

Can I pull this off without reinstalling Ubuntu?  How???  Or should I wait for Dapper Drake and start all over?[/QUOTE]


[this]("http://www.ubuntuforums.org/showthread.php?t=85182&highlight=qparted") might get u somewhere...

---

### Post by DaveRowell on 2006-01-17
Actually it isn't a question of whether these partitions CAN be created and formatted but rather a question of practicality!  

For instance can I actually make the moves without a fresh install?  am I on the right track in putting those directories on a single separate partition?

---

### Post by DaveRowell on 2006-01-19
I guess we're getting there - the system still runs! :cool: 

What I've done:
* reduced the size of XP's c:\  [hda2] by 30 odd gigs leaving MT space
* moved Ubuntu / [hda3] down next to c:
*    [hda4 is the container for logical partitions]
* moved hda4 and Ubuntu /swap [hda5] down next to /
*    leaving the order of the partitions as they were so as to keep fstab happy
* made a 5.6 gig logical partition [hda6] formatted ext3
* made a 29.3 gig logical partition [hda7] formatted fat32
* edited fstab to mount hda7 as 'winlin' with everyone having all permissions so that both OS can have full access to its data

Now all I gotta do is figure out how to convert hda6 to /home/david and copy all my stuff over - Can anyone help me with that????

Next time I boot into XP I'll change the boot order so that Ubuntu is default OS

---

