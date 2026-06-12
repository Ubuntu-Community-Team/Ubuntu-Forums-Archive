---
title: "trouble unmounting partition"
date: 2008-09-30
forum: Desktop Environments
---

### Post by jmp5167 on 2008-09-30
I am new to linux and am currently dual booting with xp.  I have successfully messed with linux to the point where I want to reinstall it on my partition to start over.  So my plan of action was to delete the partition in GParted off a live-boot cd and then reinstall after a re-boot.
The problem arose when I tried to delete my partitions.  I have linux saved on my /dev/sda5 partition.  When I tried to delete it it said it had to be unmounted.  So using the command 'sudo umount /dev/sda5' I unmounted the partition which worked.  Then when I triend to delete it again I got an error that all partitions over sda5 had to be unmounted(there is only one sda6).  but using the same command I am not able to unmount /dev/sda6..  no error comes up, the terminal says the same thing it did for sda4 but when I go into GParted it says its still mounted. Any help would be greatly appreciated.

---

### Post by prshah on 2008-09-30
> **jmp5167 said:**
> 
So using the command 'sudo umount /dev/sda5' I unmounted the partition which worked.  Then when I triend to delete it again I got an error that all partitions over sda5 had to be unmounted(there is only one sda6).  but using the same command I am not able to unmount /dev/sda6..  no error comes up, the terminal says the same thing it did for sda4 but when I go into GParted it says its still mounted. Any help would be greatly appreciated.

Most likely, your sda4 is an "extended" partition. That cannot be mounted/unmounted.

Your sda6 is probably a swap partition. To "unmount" that, use the command ```
sudo swapoff -a
```

You also cannot unmount the active partition (eg, whichever partition you are currently using), so boot from the live CD to unmount these partitions (for swap, you have to use the swapoff command as above).

You can get a nice graphical view of your partitions and GUI handling by using gparted. Boot off the live CD and look in System-Administration-Partition Editor. From this, you can right click the partitions you don't want and choose "unmount" or "swapoff" (as the case may be). Once you have "removed" the partitions you don't want, click on Apply to commit your changes. 

If you want to confirm your partition structure before unmounting anything, either post back a gparted screenshot, or the output of the command below:```
sudo fdisk -l
``` (From a terminal: Applications-Accessories-Terminal)

---

