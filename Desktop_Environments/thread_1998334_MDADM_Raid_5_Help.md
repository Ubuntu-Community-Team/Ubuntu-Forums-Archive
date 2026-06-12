---
title: "MDADM Raid 5 Help"
date: 2012-06-06
forum: Desktop Environments
---

### Post by RedEyeZ88 on 2012-06-06
Hey everyone,

I wasnt sure which section to place this in, so I hope this is appropriate. I upgraded to 12.04 last night on the desktop environment. I have  a small RAID 5 setup, which is used as my NAS and everything else. For the past month or so, I have been having awkward things happen to my RAID. Everytime I checked mdadm --detail /dev/md127, I would see two devices removed on the raid. I decided by upgrading to 12.04 on a new install, that it may fix any weird things hapening by itself.

Now all of a sudden, MDADM is showing I have 2 arrays and I have NO idea why. I see md126, and md127. Can you guys please please help me put this back together into 1 array, and get one of my removed drives active? I really cannot lose my data, and do not want to destroy/rebuild the RAID with out it.

Lesson learned, multiple backups. 

I posted a picture of how far I have gotten. Please let me know how to proceed.

---

### Post by WTF_Shelley on 2012-06-06
if i was you i would pull everything off it before you start (double check you got everything), then kill it and reformat and rebuild the raid from start.  The problem might be caused if some of the drives are sleeping at different times then the others are they different manufactors also is it on a ups? raids have a $%^% fit if they have a power cut.

---

### Post by RedEyeZ88 on 2012-06-06
I would love to do that, but I cant even get the thing up or mounted to do so. I feel like there has to be away to get this back up

---

### Post by WTF_Shelley on 2012-06-06
can i get a cat /proc/mdstat


Cant promise i can help as my software raid-fu is pretty weak-sauce

---

### Post by RedEyeZ88 on 2012-06-06
sure, but all of a sudden it mounted and only 1 of the drives is removed. NO idea why, but im transfering what data I can. I dont want to rebuild the array, if i can get it working i rather do that but atleast now we have the option of destroying and rebuilding if nothing else works since i can get my data

---

### Post by RedEyeZ88 on 2012-06-06
all i did was a reboot

---

### Post by RedEyeZ88 on 2012-06-06
update: so now that it seems to randomly work, I went ahead and added the other missing drive via:

sudo mdadm --manage /dev/md127 --add/dev/sdf1

and right now it says Spare Rebuilding for that drive.

I have no idea why it suddenly works, but I def want to get this locked into working correctly. as soon as its done rebuilding ill post the proc.

is there anything else i should be posting so you guys can help look at the status of the raid? also should i reboot and see if it ceases to work again?

---

### Post by RedEyeZ88 on 2012-06-06
Here is my mdstat:


vivek@Devastator:~$ sudo cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active raid5 sdf1[2] sdb1[4] sde1[0] sda1[6] sdc1[3] sdd1[1]
      9767552000 blocks super 1.2 level 5, 1024k chunk, algorithm 2 [6/6] [UUUUUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk

unused devices: <none>

---

### Post by bjforesthowell on 2012-06-11
I'm having some similar issues as well...

root@ubuntu:/media# fdisk -l

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0db54da5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   125042687    62417920    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 14002.2 GB, 14002197364736 bytes
255 heads, 63 sectors/track, 1702336 cylinders, total 27348041728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000810fe

   Device Boot      Start         End      Blocks   Id  System
root@ubuntu:/media#

root@ubuntu:/media# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>
root@ubuntu:/media#
root@ubuntu:/dev# mdadm --create /dev/md0 --level=raid5 --raid-devices=1 /dev/sdb
mdadm: '1' is an unusual number of drives for an array, so it is probably
     a mistake.  If you really mean it you will need to specify --force before
     setting the number of drives.
root@ubuntu:/dev# mdadm --create /dev/md0 --level=raid5 --force --raid-devices=1 /dev/sdb
mdadm: at least 2 raid-devices needed for level 4 or 5
root@ubuntu:/dev# ls -al

I'd love to be able to mount this device, but I'm not getting any luck... Is anyone making any progress?

---

### Post by eyelessfade on 2012-06-11
> **bjforesthowell said:**
> 
root@ubuntu:/dev# mdadm --create /dev/md0 --level=raid5 --force --raid-devices=1 /dev/sdb
mdadm: at least 2 raid-devices needed for level 4 or 5
root@ubuntu:/dev# ls -al

I'd love to be able to mount this device, but I'm not getting any luck... Is anyone making any progress?

mdadm can't and won't let you create a raid5 with 1 disk. Minimum of disks needed for raid 5 is 3! so you can create a raid 5 with 2 disks and one missing. Which is a degraded raid.

---

### Post by bjforesthowell on 2012-06-14
I initialized the 8 disk array, and this is what shows up. No filesystem, no nothing. The only thing that shows up is the single initialized drive.

---

### Post by bjforesthowell on 2012-06-14
I ended up being able to do a 

mkfs.ext4 /dev/sdb

and it worked like a champ. I'm not able to mount the drive without messing aroudn with mdadm.

---

### Post by RedEyeZ88 on 2012-07-07
Alright, problem has randomly come back for me and I cant get it working again...not sure how to proceed.

---

### Post by RedEyeZ88 on 2012-07-07
So, in trying to fix this issue, im trying to assemble my /dev/md127

but its saying that its not in the config file. How do i fix that?

---

