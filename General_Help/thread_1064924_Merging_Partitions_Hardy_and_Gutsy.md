---
title: "Merging Partitions Hardy and Gutsy"
date: 2009-02-09
forum: General Help
---

### Post by iamhigh on 2009-02-09
Folks, Need your expert help on recovering partition from a screwed up installation.

1. Had Gutsy on 40GB hard drive
2. Upgraded Gutsy to Hardy - did not go as planned
3. Had data on Gutsy so installed Hardy on a separate partition
4. Hardy working fine.
5. Moved data from Gutsy to Hardy
6. Gutsy still remains as a ghost partition - not being used - just takes up 22 GB of valuable space.
7. What would be the Safest and easiest way to recover/merge Gutsy space into Hardy? 
         OR 
Rather do I even need to merge it? Can I just that space for installing programs and maintaining data? I cannot delete anything from it - &#263;os it says I do not have any permission. The /bin, /etc, /var folders are intact and the only place I can write anything is the home folder - so do I need to reformat and mount it?

Please refer to the screenshot at this link. --> [http://i39.tinypic.com/j5xctw.png](http://i39.tinypic.com/j5xctw.png)
Hardy is on /dev/sda6
Gutsy is on /dev/sda1

Help! I am a novice on partitioning! Step by Step details would be great.

Thanks in advance.

---

### Post by plucky on 2009-02-09
You could create a separate /home partition.See the [Psychocats guide](http://www.psychocats.net/ubuntu/separatehome)


Or

Create a separate /storage partition. See the [Psychocats guide to mounting linux partitions](http://www.psychocats.net/ubuntu/mountlinux)


Or 

Use the Ubuntu Live CD to delete the /dev/sda1 partition and then expand the Hardy partition.
Remember to backup first  before doing any of these steps,so that you don't lose your data if anything should go wrong.


Good Luck

---

### Post by iamhigh on 2009-02-10
Thanks plucky - Here is my concern though

If I do remove or partition the /dev/sda1 partition and use it for storage or home, will it affect the initial boot up? 

doesnt one of the partition have the mbr which has grub? how would I know where grub is installed?

Thanks

---

### Post by plucky on 2009-02-10
> **iamhigh said:**
> Thanks plucky - Here is my concern though

If I do remove or partition the /dev/sda1 partition and use it for storage or home, will it affect the initial boot up? 

doesnt one of the partition have the mbr which has grub? how would I know where grub is installed?

Thanks

The MBR is not part of any partition,it is located on a special part of the hard disk.Read about Grub on the [Grub Page](http://users.bigpond.net.au/hermanzone/p15.htm) Read about the different stages Grub uses to boot.

Moving the start of the Ubuntu partition would cause boot problems,as the UUID of the partition would change,and Grub uses the UUID to find the partitions.

Good Luck

---

### Post by jjpcexpert on 2009-02-10
> **iamhigh said:**
> Folks, Need your expert help on recovering partition from a screwed up installation.

1. Had Gutsy on 40GB hard drive
2. Upgraded Gutsy to Hardy - did not go as planned
3. Had data on Gutsy so installed Hardy on a separate partition
4. Hardy working fine.
5. Moved data from Gutsy to Hardy
6. Gutsy still remains as a ghost partition - not being used - just takes up 22 GB of valuable space.
7. What would be the Safest and easiest way to recover/merge Gutsy space into Hardy? 
         OR 
Rather do I even need to merge it? Can I just that space for installing programs and maintaining data? I cannot delete anything from it - &#263;os it says I do not have any permission. The /bin, /etc, /var folders are intact and the only place I can write anything is the home folder - so do I need to reformat and mount it?

Please refer to the screenshot at this link. --> [http://i39.tinypic.com/j5xctw.png](http://i39.tinypic.com/j5xctw.png)
Hardy is on /dev/sda6
Gutsy is on /dev/sda1

Help! I am a novice on partitioning! Step by Step details would be great.

Thanks in advance.
Well then move a(some) valuable file(s), install GNOME-Parted gparted and then make sure to DELETE your 7.xx Partition

---

