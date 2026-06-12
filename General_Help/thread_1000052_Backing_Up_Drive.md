---
title: "Backing Up Drive"
date: 2008-12-02
forum: General Help
---

### Post by robbied on 2008-12-02
I would like for someone to retrace my footsteps and let me know if what I've done makes sense.  I am looking to back everything up so if my drive fails or I destroy it, then I can just restore everything.

I'm using Intrepid on a HP dv6000, external drive is a Seagate
I dual boot XP and Ubuntu.  Each has its own partition on my laptops drive.

What I have done:
1.Bought 500GB external drive.
2.Used Gparted to copy and paste each partition onto the new drive
3.The external drive has the Windows, Linux, and Free Space partition.
4.I formated the free space as NTFS so both OS's can read the partition.



DOES THIS MAKE SENSE TO YOU? Also, do you for see any problems?

In the event of Windows failing on the laptop:

Boot from LiveCD and use Gparted
Delete Windows partition
Copy sdb1 (Windows on External) to sda1 (Windows on Internal)
This should be sufficient but may require GRUB reinstall....?


In the event of Ubuntu failing on the laptop:

Boot from the LiveCD and use Gparted
Delete Ubuntu partition or should I delete extended since extended was copied to External?
Copy sdb2 (Ubuntu on External) to sda5 (Ubuntu on Internal)
This should be sufficient but may require GRUB reinstall....?


Also, is this possible........

I made a tar backup of / using methods described online.
tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /


Reinstall Ubuntu in the same location

Replaced all files with backed up tar file
 tar xvpfz backup.tgz -C /

For those who reply, thanks for taking the time to give me peace of mind...:p

---

### Post by Titan8990 on 2008-12-02
I wouldn't use gparted as a backup method...


Try partimage, or if you feel comfortable with CLI dd and rsync are great tools.

---

### Post by robbied on 2008-12-02
> **Titan8990 said:**
> I wouldn't use gparted as a backup method...


Try partimage, or if you feel comfortable with CLI dd and rsync are great tools.

I was going to use partimagge or rsync, also thought about dd, but it is just SO easy to copy and paste partitions... I know it's not optimal.  It wastes a lot of disk space with all the empty space.  My question remains though.  Will this setup work?

---

### Post by laceration on 2008-12-03
You are making things too complicated for my taste.  Are you going to do manual backups or setup a crontab?  
If you want easy try sbackup.  [http://tombuntu.com](http://tombuntu.com) recently had a tutorial on it.
I don't know if backing up to and from ntfs will make for complications.  You might just backup windows from within windows.  In vista backup tools are included, but not xp.

---

### Post by robbied on 2008-12-03
UPDATE:  I thought it was necessary to include the fact that I will not be updating the backup very often.

I know this method would suck if I wanted daily or weekly backups since it's so time consuming.  I want an "archive" of the way I have things now for future use.  Please keep that in mind.  I just want to know if what I have done should work in the event of dive failure...

Thanks
Robert

---

### Post by robbied on 2008-12-04
No one can answer if this is at least feasible?  I am not too concerned with it being optimal, just doable...

If my laptop drive was to die could the copies of the partitions be used to restore everything.  Also, does the tar option work, it seems to be the best method as it is a copy of / which contains everything I have done.

---

