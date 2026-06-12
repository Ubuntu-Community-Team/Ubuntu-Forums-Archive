---
title: "Multiple Distros, How many swap partitions??"
date: 2006-01-09
forum: Desktop Environments
---

### Post by linuxden on 2006-01-09
Hi,

I have multiple distros installed on my lappy, Now each dstro hasd its own swap space... my question is do i really need to have 4 different swap partitions???

Any info would be great... It save me at least 4 gigs of disk space... Perhaps for DSL.... :o)

---

### Post by errr on 2006-01-09
no you can use the same one for all.

---

### Post by linuxden on 2006-01-09
Sweet!!! 

Thx for the quick swift response!!!

DSL here i come!!!

---

### Post by az on 2006-01-09
If you hibernate, you will lose your data if another OS uses your swap.  Suspend-to-disk writes the contents of your memory to swap...

---

### Post by linuxden on 2006-01-09
[QUOTE=azz]If you hibernate, you will lose your data if another OS uses your swap.  Suspend-to-disk writes the contents of your memory to swap...[/QUOTE]

No hibernating for me... So i am going to delete all the swaps xept 1... Is it safe to delete them?? which one do i keep??

Thx Azz

---

### Post by wpshooter on 2006-12-30
> **azz said:**
> If you hibernate, you will lose your data if another OS uses your swap.  Suspend-to-disk writes the contents of your memory to swap...

Are you thus saying that under this circumstance or perhaps others that it could possibly be better to have multiple swap paritions and if you do have multiple swap partitions, is there some determining factoring in which one is used by which O/S ?

Say if I had both Dapper and Edgy installed on the same machine, how do I assigned one swap for Dapper's use and the other for Edgy's use ?

Thanks.

---

### Post by ravenon on 2006-12-30
I believe it is all handled in /etc/fstab.

---

