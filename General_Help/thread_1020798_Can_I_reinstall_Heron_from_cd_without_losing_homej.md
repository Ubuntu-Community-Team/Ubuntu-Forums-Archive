---
title: "Can I reinstall Heron from cd without losing /home/jake data??"
date: 2008-12-24
forum: General Help
---

### Post by Johnny-Cache on 2008-12-24
After many different attempts, I have given up trying to repair what is screwed up. Can I reinstall Heron without losing my /home data?  I would like to just start from scratch, but save my data....is that possible at all?


regards

---

### Post by albinootje on 2008-12-24
> **Johnny-Cache said:**
> After many different attempts, I have given up trying to repair what is screwed up. Can I reinstall Heron without losing my /home data?  I would like to just start from scratch, but save my data....is that possible at all?

Do you have some usb-disk or DVD-writer ?
Boot from the Ubuntu installation cdrom and use the "live session, which is called "try ubuntu without installing" I think.
In a terminal run :
```

gksu nautilus

```
And start backing up /home/ to some external media or to some other partition that you're not using and not gonna overwrite during the following Ubuntu installation.
Remember that backing up to a FAT-partition will make all files executable (Thanks Bill), and this is not what you want.
Creating an archive of those files first is a good option then.

---

### Post by ugm6hr on 2008-12-24
If you have a separate /home partition, it's pretty easy.

If not, back everything up and renstall.

Remember that a lot of Gnome settings are stored in /home, so restoring or maintaining it may not be the solution.

---

### Post by albinootje on 2008-12-24
> **ugm6hr said:**
>  Remember that a lot of Gnome settings are stored in /home, so restoring or maintaining it may not be the solution.

What do you mean with this ?
If the same Ubuntu release is reinstalled, and the same username is used as before, then what problems do you foresee ?

---

### Post by Johnny-Cache on 2008-12-24
My biggest issue is that I don't have enough storage to handle all of my data.  I plan to back up MOST of it and then try to reinstall ubuntu over the same directory.  I'm just trying t figure out in advance if I will lose what's in my home directory or if it's possible to keep it in tact somehow.

---

### Post by anjilslaire on 2008-12-24
Meaning, if the problems he's experiencing are gnome settings-related, they may still be present even after a reinstall if he restores his /home directory.

---

### Post by ugm6hr on 2008-12-24
> **ugm6hr said:**
> If you have a separate /home partition, it's pretty easy.

If not - No.

---

### Post by albinootje on 2008-12-24
> **Johnny-Cache said:**
> My biggest issue is that I don't have enough storage to handle all of my data.  I plan to back up MOST of it and then try to reinstall ubuntu over the same directory.  I'm just trying t figure out in advance if I will lose what's in my home directory or if it's possible to keep it in tact somehow.

Another idea is to follow your "back up most of it", and then resize the Ubuntu partition a bit.

After making the backups, delete everything on the Ubuntu installation that you have made a backup of.
Resize the ubuntu partition, and create a new partition.
Format that new Linux partition.
Copy the data that you didn't make backups of to that new partition.
After that do a new Ubuntu installation using the old partition.

---

### Post by Johnny-Cache on 2008-12-30
Thanks for the help and the back logs of this forum.  I have fixed my problem.  Lessons learned:

The install disks for all Linux are very open to errors which will confuse any A+ guy.  Burn it slow and use the same cd drive to boot it up.

I booted off the liveCD for ubuntu with an extra hard drive installed that was formated to NTFS.  I then had to force mount it by 
$sudo mount -t ntfs /dev/sdb1 /media/disk2 -o force

my system then thanked me for being cool.

---

### Post by Johnny-Cache on 2008-12-31
Used the USB install and it saved all of my data.  Pimp'n ain't easy.

---

### Post by ugm6hr on 2008-12-31
> **Johnny-Cache said:**
> Used the USB install and it saved all of my data.  Pimp'n ain't easy.

Use a separate /home partition.

Then it is really easy.

---

### Post by anjilslaire on 2008-12-31
> **Johnny-Cache said:**
> Used the USB install and it saved all of my data.  Pimp'n ain't easy.

But *somebody's* got to do it

;)

---

### Post by sistoviejo on 2008-12-31
How to backup your partition in the same hard drive:

1 - Check the size of your home folder:
sudo du -hs /home/jake

For the following steps you will need the gparted live CD.
2 - Download gparted live CD from here: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
(Check gpodder documentation and search google for help on these steps)

3 - Reduce the size of one of your partitions. 

4 - Create a new partition larger than your home folder.

5 - Reboot into your system, mount the new partition and copy the whole home folder into the new partition.
Google for help on mounting partitions.
After you mounted the new partition in /mnt copy the whole folder into it, type: 
cp -rf /home/jake /mnt 

After that you can delete all the partitions except the new one and install on the empty space.
Make sure you don't delete the partition that you copied your home folder into when installing Ubuntu. 
Ubuntu will delete it by default on the partitioning steps so do a manual partition. 
Create a swap partition (a bit larger than the RAM on your system) and a  system partition (formatted with ext3).
You could use the new partition as /home if you want.

---

