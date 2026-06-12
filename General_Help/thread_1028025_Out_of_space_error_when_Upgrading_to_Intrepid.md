---
title: "Out of space error when Upgrading to Intrepid"
date: 2009-01-02
forum: General Help
---

### Post by otz070 on 2009-01-02
Here is the error:

[I][COLOR="Red"]Not enough free disk space

The upgrade aborts now. The upgrade needs a total of 2187M free space on disk '/'. Please free at least an additional 91.0M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.[/COLOR][/I]

Tried sudo apt-get clean and empty trash (was around 270M before)
Can't get it any smaller though.

Any possible way to make "/"drive bigger with gpartion?
My drive is 160Gib
The way It Setup the drives on ubuntu is a bit confusing (not the partitioning but the naming and setup) Maybe if someone could explain it better to me, either that or I'm getting some type of error that I don't know about.

Thanks.:D

---

### Post by prshah on 2009-01-02
> **otz070 said:**
> 
The upgrade aborts now. The upgrade needs a total of 2187M free space on disk '/'. 

Any possible way to make "/"drive bigger with gpartion?
My drive is 160Gib


Yes, you can use gparted to shrink one of the existing partitions, and then extend your "/" (root) ubuntu partition into that free space.

Here are the steps you will need to follow.

Partition activities cannot take place on a mounted hard drive. So you need to boot off the live CD.

Then, open the System-Administration-Partition Editor and right click and "unmount" any partitions which are mounted. Also right click the swap partition and choose "Swapoff".

Now that all your partitions are deactivated, you can make structural changes as wanted. 

Shrink the partition that is to the immediate right (or immediately following) your root partition by atleast 3GB. No action will take place immediately.

Now, choose to expand your "/" partition (it _won't_ be marked as "/" in the partition editor window, so you need to know which one it is beforehand; easy if you have only one linux partition) to use the freed up space.

Finally, click Apply for the changes to start.

I may take a long while for the action(s) to be completed; do not interrupt or restart your computer inbetween.

While I have personally never faced a problem with resizing and moving partitions, there is an element of risk involved, so you do this at your own risk. A backup is highly recommended (but again, personally speaking, I've never taken a backup).

If you want more detailed advice, either post a gparted screenshot or open a terminal (Applications-Accessories-Terminal) and post back the output of the following command```
sudo fdisk -l
```

Good luck!

---

### Post by Tim Sharitt on 2009-01-02
If you have freespace or another partion you can resize next to you ubuntu partition, you should be able to expand it to the required size.

---

### Post by drs305 on 2009-01-02
Edited: Forgot the 'sudo' part, as pointed out in the next post...

If you post the results of the following command we can get a better idea of your disk usage:
```

[COLOR="DarkRed"]sudo [/COLOR]df -Th | grep "/dev/"

```

Also, the following link, although you have emptied your trash, discusses methods to locate hidden trash files and other techniques to free up disk space:
[Disk Full? - Check Your Trash Bin(s)]("http://ubuntuforums.org/showthread.php?t=898573")

---

### Post by dcstar on 2009-01-02
> **drs305 said:**
> If you post the results of the following command we can get a better idea of your disk usage:
```

df -Th | grep "/dev/"

```
.......
That command will HIDE all files without user access privileges, for accurate output use:

```
sudo df -Th
```

---

### Post by otz070 on 2009-01-04
```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda3     ext3    7.6G  5.3G  2.0G  73% /
varrun       tmpfs    466M  124K  466M   1% /var/run
varlock      tmpfs    466M     0  466M   0% /var/lock
udev         tmpfs    466M   68K  466M   1% /dev
devshm       tmpfs    466M   12K  466M   1% /dev/shm
lrm          tmpfs    466M   45M  422M  10% /lib/modules/2.6.24-21-rt/volatile
/dev/sda5     ext3     58G   13G   42G  24% /home
/dev/mmcblk0p1
              vfat    2.0G  452M  1.5G  24% /media/disk-1
/dev/scd0  iso9660    665M  665M     0 100% /media/cdrom0

```


Not sure how to read this,
(Actually I know what the last two are My sd card (For backups) and CD)
Is there any free space I am missing or whatever?
------------------------------------------------------------------------
just in case I do need to resize / (which I now know is root:)Thanks!) I have about 10Gib unpartitioned free (Found this out a few days ago when I went to shrink my xpdrive and had two segments unpartitioned at a total of about 30Gib so I figured I would keep the the the 10Gib partition Just in case I couldn't figure this out)
Anyway thanks for help.

---

### Post by otz070 on 2009-01-11
Bump?:confused:

---

### Post by drs305 on 2009-01-11
If you want to repartition / to incorporate the extra 10GB of unused free space please post the results of the following, or better yet, an image of the partitions in gparted.
```

sudo sfdisk -l /dev/sda

```

---

### Post by otz070 on 2009-01-11
> Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+   6118    6119-  49150836    7  HPFS/NTFS
/dev/sda2       6119   17037   10919   87706867+   5  Extended
/dev/sda3      17038   18033     996    8000370   83  Linux
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5       6119+  16788   10670-  85706743+  83  Linux
/dev/sda6      16789+  17037     249-   2000061   82  Linux swap / Solaris

Disk /dev/mmcblk0: 62304 cylinders, 4 heads, 16 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/61/60 (instead of 62304/4/16).
For this listing I'll assume that geometry.
Units = cylinders of 1873920 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/mmcblk0p1          0+   1089-   1090-   1993604+   6  FAT16
		start: (c,h,s) expected (0,4,8) found (0,3,59)
		end: (c,h,s) expected (1023,60,60) found (988,60,60)
/dev/mmcblk0p2          0       -       0          0    0  Empty
/dev/mmcblk0p3          0       -       0          0    0  Empty
/dev/mmcblk0p4          0       -       0          0    0  Empty


What does that warning mean? something to be concerned about?

Also as an additional note the needed amount moved up when I ran it last 
from 90+/- mib to 400+/-mib

Is it recommended to repartition all 10gib to root or is there something that I can temporarly move/ uninstall to free up space  for now?
themes Icons ect programs? will these free up root space?

I'll post a sreen from gparted when I get to my hardyCD....
Unless it can be read from this info
Where exactly do I partition this to, to increase the size of root?

---

### Post by otz070 on 2009-01-17
Bump? 
(Note the Smiley in the above post from pasted terminal output is suppost to be an "8")

---

### Post by otz070 on 2009-01-23
Sorry it took so long for this:

---

### Post by otz070 on 2009-01-28
bump

---

### Post by prshah on 2009-01-28
> **otz070 said:**
> Sorry it took so long for this:

Ok from this screenshot we see that your root partition (/dev/sda3) is immediately preceeding the unallocated space, which is all good.

Boot off the live CD, right click the /dev/sda3 partition and choose unmount (if it is mounted, the "keys" icon will show if it is mounted). 

Then right click the /dev/sda3 partition and choose the Resize option; increase the size (drag the righthand side slider bar all the way to the righthand side edge) then click OK, then click Apply in the toolbar along the top.

All [earlier caveats apply]("http://ubuntuforums.org/showpost.php?p=6477747&postcount=2").

---

### Post by otz070 on 2009-02-04
:D Awesome, Thanks,  (though I am still going to do this;) and put the free space to good use)
However, now after running intrepid on another system (As I need that one to be full stable) I don't think I will be upgrading to intrepid just yet.

(Mabye a bit off topic here but just to explain my reasons for not upgrading yet for the curious....)
My main reason was to be able to get the latest realeases (stable) in deb form (from get deb) which seem to be only released for intrepid, fortunatly I have discovered a work around which is basically creating my own .deb packages with the chosen release. Yep a bit more annoying and time consuming, but worth the while if it means I wont have to worry about the freezing that I get with intrepid on my other system (which is configured the same way.) So far seems to be related to an issue with the kernal (or an associated file or something I don't code so...yep) as after there have been several updates the kernal becomes stable (same with hardy, though not as bad) so I often use older kernals, pretty much one that I feel runs stable, I stick with. Makes Sense

Anyway Thanks Extremely, as this solves one of my many problems:D

---

