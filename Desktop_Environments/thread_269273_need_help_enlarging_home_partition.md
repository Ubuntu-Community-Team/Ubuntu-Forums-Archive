---
title: "need help enlarging /home partition"
date: 2006-10-01
forum: Desktop Environments
---

### Post by finite9 on 2006-10-01
I have a small /home partition and I want to enlarge it with some space i've freed up on the same disk (deleted another partition).

How can I enlarge /home without destroying it?  I had the idea to unmount it and then use gparted to resize it, but I cannot unmount /home as it is in use.

---

### Post by devils_casper on 2006-10-01
are you using GParted CD ? 




casper

---

### Post by finite9 on 2006-10-02
I don't really understand?

I tried it all from within my session after having booted from the hard disc.

I do have an Ubuntu Live CD, but if I don't remember wrongly, Gparted is not installed as standard on the Live CD, so I would have to use the shell to do this, and that is where I got stuck.  If you could supply me with a quick guide of how I can do this from the shell, then I think I could manage it.  I realise that I have to boot from the Live CD so that I don't login as a user whereby all my start files are loaded from /Home, thereby hindering me from unmounting the partition.

---

### Post by indytim on 2006-10-02
finite9,

There are a number of different solutions to what you are attempting to do.  My favorite on doing partiton work is to use GParted Live.  Using this utility (after burning the iso to a CD) will allow you to do your partition work from a boot.  I have also found that it is a good utility to have in the "tool chest".  

If you're interested, here's the link for the GParted Live site.

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

Hope this helps.  Good Luck,

IndyTim

---

### Post by finite9 on 2006-10-02
Thanks a lot for the link!  Will give this a try tonight.

Would be nice to know how to do this from the shell, so that I didn't need extra CD's but thats just me.

Thanks!

---

### Post by finite9 on 2006-10-03
Well, it worked and it didn't work.  The ISO is great and does what it says on the box, but I cannot assign free space from one primary partition to another primary partition :(  The free space is not adjascent to the partition I want to enlarge either and it wont let me move the /home partition or resize it.  Bummer.

I suppose it's only useful if you've created several extended partitions in the same primary partition and have space left over to assign to any of those extended partitions, but as I have Windows, which stupidly creates a new primary partition for every drive letter, I cannot do much about this without re-installing Ubuntu (which at the moment is looking rather tempting considering other issues I have).

---

### Post by CatKiller on 2006-10-03
Really? I thought Windows generally made Logical partitions in an Extended partition by default, after the first Primary partition. Maybe it's a newer-Windows thing.

Anyway, if you've created space elsewhere on the drive, can't you move the other partitions so that there is space after your /home partition? It's been a while since I used GParted, so I can't remember for sure. And it is included on the Dapper Live cd. Don't know about earlier versions.

---

### Post by finite9 on 2006-10-04
nope, I tried moving /home and the option for move/resize is simply greyed out.

I have 4 primary partitions on the disk...3 made by windows:

1 service partition for the laptops recovery mechanism
1 partition for C: as NTFS
1 for D: as FAT32

I 'resized' D: drive from 24GB to 8GB (dropped partition and recreated smaller D: partition) which created my free space after primary partition #3, but before primary part. #4 (Linux).

Then fourth is my Linux primary partition, within which there are several extended partitions for /, /Home, /swap and /tmp

I tried to create a new JFS partition in the free space and it said that I could not have more than 4 primary partitions.

I tried to 'move' the first extended partition within primary partition #4 ( root ) as the free space was adjascent to this partition, but it would not let me.  I could not move or resize any partition apart from primary #3, my resized D: drive, as the free space was adjascent to this partition.

---

### Post by CatKiller on 2006-10-04
You'll need to move the Extended partition (the box around your Linux partitions) to the beginning of the available space, and then resize it to the right. And then move the Linux Logical partitions within this now larger box to have space to the right of the one you want to resize. You can't make them bigger than the box they're in.

The other possibility is that you're using an older version of Gparted. I understand that the ability to move an ext3 partition is relatively recent. Perhaps you could try a newer version?

---

### Post by finite9 on 2006-10-04
Aha, that could explain things.  I right clicked on the partition in question, whether it was /hmoe, D: or / but I didn't realise you could select the box containing extended partitions and move that!  I will give it a try tonight.

I have the latest version of GParted Live..downloaded/burnt it 2 days ago.  I only have JFS partitions--no ext3.

---

### Post by finite9 on 2006-10-09
Didn't work :(  Gparted successfully moved the free space to the extended partition as suggested, and I moved my / and /home partitions to the left of the free space, so that it was directly adjascent, to the right hand side of my /home partition.  Then came the errors...

Partition type JFS does not support growing!!

Dang.  I chose JFS over ext3 because I perceived IBM JFS as being a more feature rich/better developed FS over ext3.  If I had known that it didn't support what I regard as quite an easy to implement feature then I would never have chosen JFS.  I originally wanted XFS but there is very little support for it...Ubuntu does not fully recognise it in all instances.

I would love to be able to use Sun ZFS if it was available.

Is ext3 more feature rich than JFS?  Can an ext3 partition be grown?

---

