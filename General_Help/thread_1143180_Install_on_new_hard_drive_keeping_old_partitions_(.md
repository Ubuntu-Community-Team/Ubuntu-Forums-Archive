---
title: "Install on new hard drive keeping old partitions (windows)"
date: 2009-04-29
forum: General Help
---

### Post by manolo_asdf on 2009-04-29
hi,

currently I have a 60GB harddrive (NTFS+FAT partitions). For developing work I want to switch to Linux/Ubuntu, still I want to keep windows for applications reasons.

For that I bought a new harddrive 280GB. Is it possible to move the 60GB with same setup to the 280GB harddrive and use the rest for linux partition? 

What is the best way to do this? I already backuped with partimage and partition table, so I guess somehow I can move my stuff to the bigger harddrive. Maybe I can exactly move partition table and both partitions with partimage to the new harddrive and let Ubuntu installation do the rest, which would recognize the missing 220GB and ask what to do with it?

Or are there other tools to accomplish my task?

thanks.

---

### Post by Mze on 2009-04-29
check this [tutorial]("http://ubuntuhowtos.com/howtos/move_system_partition_to_new_hard_drive_larger_partition") out.

you may want to use [clonezilla]("http://clonezilla.org/") once you've read the tutorial

---

### Post by nacho32 on 2009-04-29
> **manolo_asdf said:**
> hi,

currently I have a 60GB harddrive (NTFS+FAT partitions). For developing work I want to switch to Linux/Ubuntu, still I want to keep windows for applications reasons.

For that I bought a new harddrive 280GB. Is it possible to move the 60GB with same setup to the 280GB harddrive and use the rest for linux partition? 

What is the best way to do this? I already backuped with partimage and partition table, so I guess somehow I can move my stuff to the bigger harddrive. Maybe I can exactly move partition table and both partitions with partimage to the new harddrive and let Ubuntu installation do the rest, which would recognize the missing 220GB and ask what to do with it?

Or are there other tools to accomplish my task?

thanks.

 what i would do in your case if you just need more space for the windows part I would partition the new hard drive using Gparted download the iso burn to disk, create a new partition on the new drive, and partition the rest using gparted for linux and install Ubuntu , now you will have a dual boot system, I run a triple boot windows 7 beta ,xp,ubuntu it rock having all 3 :)

---

