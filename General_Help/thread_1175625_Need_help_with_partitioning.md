---
title: "Need help with partitioning"
date: 2009-06-01
forum: General Help
---

### Post by zortec on 2009-06-01
I want to split up the Windows partition I created and use 1-2GB for swap and the rest for root. Do I want a swap file?  I know in Windows, the general consensus was to have your swap file be 1.5x physical memory.  This is probably not true in Linux, but I would like to get a few opinions about whether or not one should use swap.  The following is my disk layout:

SCSI1 - 320GB
#1 primary 104.9GB
#2 primary 31.5GB
pri/log 83.8GB

Should I use a manual or guided install? The guided install used 7.5GB for swap and 138GB or such for root. If I go with manual, I have to decide if the partition will be at the beginning or front of the drive.  Does it really matter?  The screen also has a lot of other choices to make about the partition and I am not sure what is best.

Can anyone offer some assistance?

---

### Post by dvl300 on 2009-06-01
i would say go for a manual install 

use gparted or the partitioner provided on the ubuntu live cd and resize your windows partition then create your swap partition 

hope this helps!
:)

---

### Post by raymondh on 2009-06-01
> **zortec said:**
> I want to split up the Windows partition I created and use 1-2GB for swap and the rest for root. Do I want a swap file?  I know in Windows, the general consensus was to have your swap file be 1.5x physical memory.  This is probably not true in Linux, but I would like to get a few opinions about whether or not one should use swap.  The following is my disk layout:

SCSI1 - 320GB
#1 primary 104.9GB
#2 primary 31.5GB
pri/log 83.8GB

Should I use a manual or guided install? The guided install used 7.5GB for swap and 138GB or such for root. If I go with manual, I have to decide if the partition will be at the beginning or front of the drive.  Does it really matter?  The screen also has a lot of other choices to make about the partition and I am not sure what is best.

Can anyone offer some assistance?

Hi,

If you do plan to use hibernate and/or suspend, then a swap partition at 1.5X ram makes' sense.  If no intentions (i.e. "heck, I shutdown the computer all the time") then .5 of ram is OK.  Also swap partition is more efficient that a swap file and the swap can be at the end of the partition.

Guided is Ok.  You can use the slider to move the partitions to suit your needs and ubuntu will do the rest, including the swap.  If you're up to it and need it, a manual install gives you the ability to create separate partitions, make it logical, etc, to suit complicated needs.  

My thinking is that unless needed (i.e. "I'm out of partition and need to do an extended with various logicals inside it"..) go for an install that is as simple as possible.

Some questions to consider :

Did you try out the liveCD and make sure that your hardware (wifi, sound, etc) work with the distribution?

Do you plan to have a separate /home partition?

Regards,

---

### Post by zortec on 2009-06-01
> If you do plan to use hibernate and/or suspend, then a swap partition at 1.5X ram makes' sense. If no intentions (i.e. "heck, I shutdown the computer all the time") then .5 of ram is OK. Also swap partition is more efficient that a swap file and the swap can be at the end of the partition.

I was not going to use hibernate, but I did want suspend.  

> Some questions to consider

Did you try out the liveCD and make sure that your hardware (wifi, sound, etc) work with the distribution?

Do you plan to have a separate /home partition?

I was unable to get the Live CD to boot.  That is why I am using the minimal CD to install Ubuntu.  

The only benefit that I could see in a separate /home partition is if you are going to have multiple users.  Is there any other advantage?

---

### Post by drs305 on 2009-06-01
> **zortec said:**
> The only benefit that I could see in a separate /home partition is if you are going to have multiple users.  Is there any other advantage?

The separate /home can be an advantage if you intend to do upgrades to future versions via the CD (clean install). In that case, you can keep your /home partition during the upgrade. This preserves your user configuration files, which contain all the tweaks and specialized settings you may have created along the way. If you do network upgrades (online), your /home settings are retained during the upgrade whether or not it is located on a separate partition.

---

