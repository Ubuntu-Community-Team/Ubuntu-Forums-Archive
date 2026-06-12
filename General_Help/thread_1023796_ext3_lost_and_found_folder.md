---
title: "ext3 lost and found folder"
date: 2008-12-28
forum: General Help
---

### Post by bryncoles on 2008-12-28
just a quick question - i got a brand spanking 1 terabyte (or whatever the term is) external hard drive for xmas,  split it into two partitions one as ext2 and one as ex3 (no i dont know why i picked different formats either). and am now backing my stuff up on it. 

i noticed though that while each drive says its 500 gigs, it also says theres about 23gigs in use, for the 'lost and found' folders. 

what exactly is this folder, why is it 23 gigs and whats it for? do i need it, or can i reclaim those 23 gigs?

hope everyones having a good festive xmas (bah, humbug!)

cheers guys.

---

### Post by ushimitsudoki on 2008-12-28
[/lost+found]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html")
> As was explained earlier during the overview of the FSSTND, Linux should always go through a proper shutdown. Sometimes your system might crash or a power failure might take the machine down. Either way, at the next boot, a lengthy filesystem check (the speed of this check is dependent on the type of filesystem that you actually use. ie. ext3 is faster than ext2 because it is a journalled filesystem) using fsck will be done. Fsck will go through the system and try to recover any corrupt files that it finds. The result of this recovery operation will be placed in this directory. The files recovered are not likely to be complete or make much sense but there always is a chance that something worthwhile is recovered. Each partition has its own lost+found directory. If you find files in there, try to move them back to their original location. If you find something like a broken symbolic link to 'file', you have to reinstall the file/s from the corresponding RPM, since your file system got damaged so badly that the files were mutilated beyond recognition. Below is an example of a /lost+found directory. As you can see, the vast majority of files contained here are in actual fact sockets. As for the rest of the other files they were found to be damaged system files and personal files. These files were not able to be recovered. 

The [Linux Filesystem Hierachy]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html") is pretty well documented, but lots of distros don't follow it exactly.

---

### Post by bryncoles on 2008-12-28
ah, so the lost and found is quite an important folder then? i presume that ubuntu automatically picks the optimum size for this folder two, and therefore i shouldnt really try and compress it any... just seems a little much to have set aside for system failures (i guess i'd change my mind when/if i suffer a system failure...)

---

### Post by bryncoles on 2009-01-01
so... this external hard drive i have... is it necessary to leave the lost and found folder as it is?  what would be the implications / risks of trying to move / remove / resize (shrink) it?

---

### Post by snova on 2009-01-01
I don't know why it would be 23 GB... What's inside it? (You'll need root permissions to inspect it)

```
gksudo nautilus /media/disk
```

(or wherever the disk is)

---

### Post by louieb on 2009-01-01
lost+found You can delete it. but like a bad penny it will keep coming back.

Its created by fsck. fsck uses it to put problem files and folders in. Might want to take a look in it before deleting.

The 23GB used might also be the ext3 journal. If I remember right ext3 will use about 5% of a partitions space for the journal.

---

### Post by jerome1232 on 2009-01-01
Well not quite, ext3 puts aside 5% of the partition aside for root, the journal will use additional space besides that. I guess the 5% also helps prevent fragmentation on very full drives. You can use tune2fs to change the amount of space allocated for root.

---

### Post by Locutus_of_Borg on 2009-01-01
if you are just using it for storage of files, you don't need the lost+found folder, and you don't need to run fsck on it either
```
cd /media/disk
rm -rf lost+found
umount /media/disk
tune2fs -c 0 /dev/sdb1
```
will get rid of both 'problems' (or course change what values are there)

---

### Post by bryncoles on 2009-01-02
yeah, the external drives are just used for external storage - they're hot-plugged only as-and-when needed, so it looks like Locutus_of_Borg's input is what im looking for. 

now: just to check (im paranoid about rm/rf commands), none of this will bork any data that's currently on the drive, will it? last thing i want to do is lose data of course!

assuming i get the all-clear, ill try this out later on, reclaim the 46 gigs which ext3 has stolen from me!

;)

cheers again everyone!

---

### Post by bryncoles on 2009-01-11
done this now, but removing the lost and found folder doesnt seem to have cleared up any space... anyway to check where my free space is? is it likely to he in a secret, hidden trashes folder?

---

### Post by jerome1232 on 2009-01-11
du should be able to show you where the space is, change /path/to/mountpoint to the real mount point of course.

```
du -hx --max-depth=1 /path/to/mountpoint
```

---

