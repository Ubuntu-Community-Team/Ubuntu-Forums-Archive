---
title: "use entire disk for Ubuntu"
date: 2009-04-10
forum: General Help
---

### Post by sadicote on 2009-04-10
I had installed Ubuntu alongside Windows on a 40 GB of 160 GB partition. I removed Windows after that as soon as began to feel a little bit sure of myself. Since then, i have, with your help, upgraded to Jaunty, installed a ton of applications and even the Nvidia 185.19 Beta. I now wish to use the entire 160 GB for my upgraded Ubuntu. Sudo fdisk -l gives 
sade@sade-desktop:~$ sudo fdisk -l
[sudo] password for sade: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x556b556b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda2            1276        6374    40957717+   f  W95 Ext'd (LBA)
/dev/sda3            6375       19457   105089197+  83  Linux
/dev/sda5            1276        1667     3148708+   7  HPFS/NTFS
/dev/sda6            1668        6175    36210478+  83  Linux
/dev/sda7            6176        6374     1598436   82  Linux swap / Solaris
sade@sade-desktop:~$ 

I got preoccupied with Blender, didn't get around to studying my Linux basics tutorials (unforgivable, i know) and have no idea what to do with the above information. Could you please guide me?  I have attached a screenshot of my Disk usage analyzer.

---

### Post by acreech on 2009-04-10
If you are wanting to remove that one windows partition and then resize another partition you need to use the live cd. boot into the live cd and then use gparted. System>Admin>Partition editor

You cant use the partition editor on your main hard drive because it is mounted, but if you use the live cd then gparted should be able to help you manipulate it.

---

### Post by sadicote on 2009-04-10
But my live CD is Intrepid..and i want to resize my Ubuntu installation to use the entire 160 GB

---

### Post by acreech on 2009-04-10
> **sadicote said:**
> But my live CD is Intrepid..


That won't matter. You are only using the live cd to access Gparted. Not to re-install your ubuntu system. You need to use a live cd so that your main drive won't be mounted.

---

### Post by sadicote on 2009-04-10
Used live CD, went to partition editor, all i could do was shrink the 102 GB partition, the option to increase my Ubuntu partition which is /dev/sda6, remained grayed out. I have a systemrescue CD. Can i make a bootable CD of my Ubuntu installation with it, and if so, how?

---

### Post by sadicote on 2009-04-10
Please tell me when i am being a pest...:lolflag:

---

### Post by acreech on 2009-04-10
> **sadicote said:**
> Used live CD, went to partition editor, all i could do was shrink the 102 GB partition, the option to increase my Ubuntu partition which is /dev/sda6, remained grayed out. I have a systemrescue CD. Can i make a bootable CD of my Ubuntu installation with it, and if so, how?

It shows that your 98.45 GB is Unallocated. Try clicking on that in the list and then clicking new. A window should pop up that will let you select the file format type that you want (ie ext3, ......) 

Or if you want to expand one of your partitions then click on that particular partition (such as one of your other ext3 partitions). then click on resize/move. then just resize it to absorb the unallocated amount. 

If this does not work for you, then I don't know. I also am not sure how to make a bootable cd.

---

### Post by sadicote on 2009-04-10
My /dev/sda6/ didn't have the option to absorb the unallocated space. Thanks for trying, not to worry, we will find some way, i am sure...

---

### Post by Alias1407 on 2009-04-10
What you want to try and do is delete the windows partition so it is unused space and then extend the ubuntu partition onto that unused space.

Use gparted to do it.

---

### Post by CatKiller on 2009-04-10
> **sadicote said:**
> Used live CD, went to partition editor, all i could do was shrink the 102 GB partition, the option to increase my Ubuntu partition which is /dev/sda6, remained grayed out. I have a systemrescue CD. Can i make a bootable CD of my Ubuntu installation with it, and if so, how?


You've got all sorts going on there. Your Windows partition is only 3GiB, but you appear to have all sorts of other partitions sitting around doing nothing. What are sda1 and sda3? They don't appear to be used.

The reason you can't expand sda6 is because it's contained within sda2 (an extended partition) and the reason you can't expand sda2 (which would then let you expand sda6) is because sda3 is in the way. Either delete sda3 (if you don't use it) or move it all the way to the right. Then expand sda2 (the cyan box around sda5 and sda6) so that it takes up the unallocated space. Then move sda7 to the right end of sda2 (you may need to turn swap off, since this is your swap partition. If you can't do it within that version of GParted, **sudo swapoff -a** in a Terminal should do it). Then expand sda6. You should probably hit Apply between each of the steps. It's all quite straightforward; it's just moving boxes around.

---

### Post by sadicote on 2009-04-10
Thanks a lot, i have deleted sda3, please could you bear with me awhile and explain "expand sda2 so that it takes up the unallocated space. Then move sda7 to the right end of sda2"?
It would take me ages to get back the system that i have now if i messed up anything.

---

### Post by CatKiller on 2009-04-10
Sure thing. sda2 is the light blue box around sda5, 6 & 7. Click on it to select it, either in the list of partitions or in the graphical display. Select Resize/Move. This will bring up a dialogue that shows you the size of the partition and how much space there is either side. All the free space is to the right of this partition, so you want to make it bigger by dragging the right hand end all the way to the right. This will resize it so that it takes up all the available space. The unallocated space will then be inside sda2, after the other partitions. Hit Apply, and it will do this operation. It is possible to queue up all the operations that you want to do, but a number of people suggest doing them one at a time. I've not noticed any difference either way.

Then you'll have a large extended partition with not much in. You'll want to do the same sort of operation to sda7 as you just did for sda2, but this time you don't want to make it any bigger, you just want to move it. You'll do this by dragging the centre of the partition all the way to the right. Since this is your swap partition, it might have been automatically mounted to improve performance. If this is the case, this partition will have the lock icon on it showing that you can't change it, and you'll need to follow the instructions I gave you earlier to unmount your swap partition. Hit Apply once you've moved your swap partition to the right. If the performance difference is extreme, you can turn the swap back on after you've done this operation by using **swapon** instead of **swapoff**.

So now you'll have a large extended partition with not a lot in, but with your swap partition all the way to the right. The next step is to make your / partition bigger, so that it takes up all the unallocated space, which by this time should be to the right of sda6. Using the same Resize/Move dialogue that you used to make sda2 larger and move sda6, you'll expand sda2 to the right as much as you can. Hit Apply.

You should now have your small sda1 and a large sda2 that contains your small NTFS sda5, a large sda6 for use in Ubuntu and your swap partition sda7 right at the end. Reboot into your normal Ubuntu environment, and you should find that you have plenty of free space.

---

### Post by sadicote on 2009-04-10
Booted from live CD, went to partition editor and clicked on sda2. All options remain greyed out. I had also deleted sda1, hope that is not the cause.

---

### Post by CatKiller on 2009-04-10
Deleting sda1 could potentially give you problems with GRUB, since it numbers the partitions differently. I've not done it, but I can't say for sure. If it does turn out to be a problem, I suspect that it's just a case of changing (hd0,1) to (hd0,0) in your menu.lst. If you get stuck, someone here should be able to help you.

It seems likely that sda2 is locked because sda7 is mounted. If the version of GParted has the option, you can right click on sda7 to unmount it. If not, it's the swapoff command that I gave you earlier.

---

### Post by sadicote on 2009-04-10
Right clicked on sda7, turned swapoff, no joy. Am downloading the Gparted live CD iso. Maybe it will have more options than the Ubuntu live CD partition editor. Will let you know tomorrow how it goes. Thanks.

Yaabaa-daabaa-doo! Stayed up all night but did it--had to delete the swap partition, after that i followed your instructions and now Ubuntu rules my disk. Slight problem though, a file check in recovery mode showed 2.7% non-contiguous and during boot i get a red fail sign next to Starting Firestarter. Is that huge? But hey, computer seems to working fine so thanks again.:guitar:

---

### Post by CatKiller on 2009-04-11
> **sadicote said:**
> Right clicked on sda7, turned swapoff, no joy. Am downloading the Gparted live CD iso. Maybe it will have more options than the Ubuntu live CD partition editor. Will let you know tomorrow how it goes. Thanks.

Ah. I guess if you unmount a partition outside of GParted, you need to manually refresh the list of partitions for it to notice. You can do this by restarting GParted, or probably just by selecting the drive again in the drop-down box in the top-right corner.

> Yaabaa-daabaa-doo! Stayed up all night but did it--had to delete the swap partition, after that i followed your instructions and now Ubuntu rules my disk. Slight problem though, a file check in recovery mode showed 2.7% non-contiguous and during boot i get a red fail sign next to Starting Firestarter. Is that huge? But hey, computer seems to working fine so thanks again.:guitar:
I haven't used Firestarter, so I couldn't say.

A small amount of filesystem fragmentation is fine. It shouldn't affect performance. And Linux filesystems don't tend to become very fragmented over time in the way that Windows filesystems do.

Without swap, you may find that your computer's performance is affected, and you won't be able to Hibernate the computer (since that puts the contents of your RAM into the swap). If you find that this is a problem, there are instructions [here ]("https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?")on how to make a swap file, or you can create a new swap partition in GParted and add the details of that partition to your /etc/fstab to enable it. Twice the amount of RAM up to a maximum of 2 GiB is the standard rule-of-thumb for the size of your swap, but if you want to Hibernate your computer it will need to be at least as large as the amount of RAM you have.

---

### Post by sadicote on 2009-04-11
I created a new swap immediately after that from the unallocated left by the earlier deletion; 2.18 GB and turned 'swapon' from the context menu. You may think of this as a small thing but i feel as if i have learned a world of things in this thread. Sorry if i am being repititious, but thanks.

---

