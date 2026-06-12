---
title: "How to format a ntsf partition to ext3"
date: 2005-09-03
forum: Desktop Environments
---

### Post by yhotg on 2005-09-03
hi again.

i would like how to formatt a partition from ntfs to ext3 
i was going to use qtparted but i saw there's a bug report 

thank u

---

### Post by AmpCoder on 2005-09-04
[QUOTE=yhotg]hi again.

i would like how to formatt a partition from ntfs to ext3 
i was going to use qtparted but i saw there's a bug report 

thank u[/QUOTE]
 I am also wondering how to do this as well.  I have searched Google as well as this forum, and I haven't found anything useful.  If anyone knows how to do this, I would like to know as well.

---

### Post by yhotg on 2005-09-04
well, i wanted to say that i would like "to know" how to...
lol

and what about the same partition after i formated it to fat32 in windows?
is that easier?

---

### Post by AmpCoder on 2005-09-04
[QUOTE=yhotg]well, i wanted to say that i would like "to know" how to...
lol

and what about the same partition after i formated it to fat32 in windows?
is that easier?[/QUOTE]
 When I searched Google, I couldn't find anything on FAT partitions either, I had the same idea you did, but I guess you are not able to do it with FAT either.

---

### Post by yhotg on 2005-09-04
[QUOTE=AmpCoder]When I searched Google, I couldn't find anything on FAT partitions either, I had the same idea you did, but I guess you are not able to do it with FAT either.[/QUOTE]

nop , didn't work  :? 

u looked that qtparted program? or gparted?

---

### Post by mlomker on 2005-09-04
If you intend to blow away the data then use fdisk to delete the ntfts and create a new linux partition, followed with mke2fs to format the new partition.  You'll obviously need to change the device specified to reference the proper disk and then the proper partition (fdisk -l will list them):

fdisk /dev/hda

mke2fs -j /dev/hda1

---

### Post by yhotg on 2005-09-04
[QUOTE=mlomker]If you intend to blow away the data then use fdisk to delete the ntfts and create a new linux partition, followed with mke2fs to format the new partition.  You'll obviously need to change the device specified to reference the proper disk and then the proper partition (fdisk -l will list them):

fdisk /dev/hda

mke2fs -j /dev/hda1[/QUOTE]

hey thank u.
now, is there any need to unmount the partition first?

---

### Post by az on 2005-09-04
[QUOTE=yhotg]hey thank u.
now, is there any need to unmount the partition first?[/QUOTE]
Yes.

---

### Post by yhotg on 2005-09-04
[QUOTE=azz]Yes.[/QUOTE]

did it, thank u very much

it when fine, but then i tried to change the mount point and now i have to different places like if linked

one is the original : /media/down1
the second is the one i tried to make changing fstab and doing mkdir: /down1

bizarre.
i tried to go back but they r still there, both of them

---

### Post by mlomker on 2005-09-05
[QUOTE=yhotg]i tried to go back but they r still there, both of them[/QUOTE]

A mount point is just a directory, so delete the one that you don't want...unless i'm not understanding what you're talking about:

rmdir /media/dontwantit

---

### Post by yhotg on 2005-09-05
[QUOTE=mlomker]A mount point is just a directory, so delete the one that you don't want...unless i'm not understanding what you're talking about:

rmdir /media/dontwantit[/QUOTE]

sudo rmdir /media/dontwantit ???

and what about the partition is mounted or something like that?
and what about the dir is not empty?

i tried , i really tried to get it out of my system, but it don't  want to go

update:
er... forget it. sometimes, some days u know your mind is not working..., 
i am blushing ok, ...

i was doing 
rmkdir /media/....
oh well....
thank u

---

