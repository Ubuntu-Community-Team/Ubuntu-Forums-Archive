---
title: "Resized my Ubuntu partition from windows=&gt; problems."
date: 2006-06-11
forum: Desktop Environments
---

### Post by jx2150 on 2006-06-11
Hello,
 
So I am dual-booting XP and Dapper, and wanted to give more space on my hard drive to Dapper. So I resized the partitions accordingly from within XP. It went well.
 
However, now get ext2-FS errors when Ubuntu loads, and gnome is no longer loading/present upon boot. [COLOR=red]<--FIXED[/COLOR]
 
Whats the problem here?
 
[COLOR=#ff0000]What actually is happening is that the new space that was added to my linux/ext2 partition is shown as used/occupied space on the partition. [/COLOR][COLOR=red]**_<--NOT FIXED_**[/COLOR]
 
Thanks,
Jack

---

### Post by angusvitamin on 2006-06-11
it happened to me once. I don't know exactly how to fix it, you problably have to set your grub, but wat i did was, i went into recovery mode, if i m not mistaken, it gave me a little error message and guess what, it fixed itself and gave me a message like "moved partition from block 8 to block 1". Hope it helps, hopefully somebody who actually knows how to fix it will be able to help

---

### Post by jx2150 on 2006-06-13
Hi, thanks for the input.. and actually the very same thing happened to me after I rebooted a couple times.

However, the disk size when I go into disk 'Disks' still remains to be the same size it was before. It is not showing the new space.

Is there a way I can 'rescan' or something to get the system to 'realize' what size the partition actually is?

[COLOR="Red"]EDIT: What actually is happening is that the new space that was added to my linux/ext2 partition is shown as used/occupied space on the partition. Why would that be?[/COLOR]

thanks
-jx

---

### Post by jx2150 on 2006-06-14
So does anyone know if I can regain this space that is apparently mis-labeled?


or should i start over with this partition?

Thanks,

Jack

---

### Post by jx2150 on 2006-06-14
Maybe I am not explaining this fully understandably.

[IMG]http://static.flickr.com/60/167260149_d88346bd56_o.jpg[/IMG]

Partition 2 of hda is my ext2 root partition.

So, before the resize, Partition 2 was only about 7gigs.

After, it is about 18gigs.

However, all of the additional size is "used" for some reason. Although it actually is not, so it is just inaccessible.

Does anyone have any ideas?

-Jack

---

### Post by Amon_Re on 2006-06-14
What does fsck say?

---

### Post by jx2150 on 2006-06-14
```
root@0[knoppix]# fsck /dev/hda2
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda2 is mounted.

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

EXT2       : clean, 170545/1015808 files, 1643915/2028206 blocks
root@0[knoppix]#                                                     
```

---

### Post by jx2150 on 2006-06-19
...still looking for a solution to this problem.

---

### Post by jx2150 on 2006-06-20
Somebody help me out, I am getting desperate now...

---

