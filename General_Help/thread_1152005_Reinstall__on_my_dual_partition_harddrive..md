---
title: "Reinstall  on my dual partition harddrive."
date: 2009-05-07
forum: General Help
---

### Post by basics on 2009-05-07
Hi,

 My dell desktop has 2 partitions. on one of these partitions I want to reinstall ubuntu. I do not know how to distinguish one partition from another. Both partitions have the same amount of space (Each partition has half of the total hard-drive.)

Can someone teach me how to understand which partition is which in the manual install portion of the partitioner?

The other partition must remain. All of my important files are there.

Please walk me through this step by step. I know somethings about ubuntu but I am no master at all. 

Keep it simple for me to understand.

Thanks.`

---

### Post by Dngrsone on 2009-05-07
What is on the partition you want to keep?  I mean, if you have Windows installed on that partition, then it would be easy to distinguish as the partition type would be NTFS or FAT32.

If it is data, such as your old /home directory, then that might be a litle tougher to distinguish.  Best bet would be to check your /etc/fstab on the Ubuntu that you are reinstalling, which could be problematic, since I assume you have a reason for reinstalling other than just for the heck of it.

I suppose you could boot the Live CD, mount one partition and see what there is to see and then do the other to verify what you are looking at is correct.

Once you know which partition is which, then the installation should go pretty good.

---

### Post by basics on 2009-05-07
Thanks for the reply.  :)

I have 9.04 and 8.04 on my system. This is why I had to ask. It is not simple to see which install is the one I would like to format and reinstall 9.04 on.

I need the other install of ubuntu because all of the pictures that are important to my family are there. 

If someone can give me advise as to how I can move those pictures and other docs then i would just run a new install on the hole of my system. I do not have any CDs or a USB drive to transport my data. Is there a site that would hold my files for a few hours?

---

### Post by Dngrsone on 2009-05-07
Boot into 8.04 and look at your /etc/fstab file.  Find the entry that mounts root (/) and see what device number it is (likely /dev/sda1).  You will then know which partition is the one to keep.

If you are nuking the 9.04 partition to reinstall, how about using something like gparted from within the 8.04 install to repartition the remainder of your drive?  You could create a smaller partition to store your data on (maybe mount it as /media) and then rebuild the rest of the drive during the installation process (remembering to tell install to name the /media partition you left intact).

---

