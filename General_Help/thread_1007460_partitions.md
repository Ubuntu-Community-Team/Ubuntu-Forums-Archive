---
title: "partitions"
date: 2008-12-10
forum: General Help
---

### Post by Magnus¤4 on 2008-12-10
Have a 40 GB single disc on which I have both Win XP and Ubuntu 8.10 installed. Now to the problem: my plan was to use xp for most of the time since it actually works best with my graphic hardware, but I also want ubuntu because it&#347; good with wireless networks, so when installing ubuntu I chose to set the partition for ubuntu to only 11 GB and the rest for xp, but I guess since Im not very good with this I did it the other way around and now xp has only 11 GB and ubuntu the rest.... :( 

It now looks like this when looking at it in Gparted:
ntfs         10.25 GB
extended     27.01 GB
ext3         25.85 GB  used 2.84 GB
linux-swap   1.16  GB
 

My question is: how can I keep both OS but still make more space available to xp? Use a partitioner and move some GB from ubuntu-partition to xp-partition? Is this possible? Very happy for some help... :)

---

### Post by Titan8990 on 2008-12-10
Unless that 2nd partition labeled as "extended" is a system recovery drive, you should be able to just format that in NTFS and use it for both OS.

---

### Post by plucky on 2008-12-10
> **Titan8990 said:**
> Unless that 2nd partition labeled as "extended" is a system recovery drive, you should be able to just format that in NTFS and use it for both OS.

That is a primary partition that contains the two linux logical partitions.

[color=red]Always backup your data before doing any partition resizing[/color]

Boot the Live CD or use the [Gparted Live CD](http://gparted.sourceforge.net/index.php).

1)Shrink the Linux 25.85Gb partition down to 10Gb.This will shrink the rear of the partition.

2) Move the partition to the right to take up the unallocated space created in the first instruction.(This could take a long time,as it has to move all the data as well)

3) Shrink the extended partition so that there is no unallocated space within the partition.

4) Grow the NTFS partition into the unallocated space created in step 3.

Be aware,that when you move and resize partitions,the UUID of the partition changes,which could cause problems booting.Use the Live Cd to fix these problems.

Good Luck.

[color=blue]p.s It might be quicker to just re-install Ubuntu with the correct partitions.[/color]

---

