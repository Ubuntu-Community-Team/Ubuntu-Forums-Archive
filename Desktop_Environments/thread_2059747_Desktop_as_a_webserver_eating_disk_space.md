---
title: "Desktop as a webserver eating disk space"
date: 2012-09-18
forum: Desktop Environments
---

### Post by AvengerX9 on 2012-09-18
My Ubuntu desktop edition is also my webserver and Im a newbien too all Linux. My drive is not big, like 40GB something and Ubuntu is eating lots of the disk space. Im almost out of disk space allready and Im getting the "battery state" problem at startup from time to time. So how can I free up disk space and how can I move the var/www folder to the other HD so it can serve the contents of my website from there ?

Hope you understand :) Thanks

---

### Post by JKyleOKC on 2012-09-18
You can probably free up a significant amount of disk space from the directory /var/log (which contains almost all of the system log files, and some of them can grow large quite rapidly).

When you look in this directory, you will see many files with names ending in ".gz"

These are archive copies of older logs, and in almost every case you can get rid of them. They are owned by the super-user, though, so you have to use "sudo" (at the command line) or gksudo (from the GUI) to remove them. Be very careful when doing so, since these commands allow you to destroy your system by accident! And leave the files that do not end in ".gz" alone, since many of them are in use by the system, behind the scenes.

Moving /var/www to another disk can be a bit complicated, so I'll leave the instructions on how to do so for someone else to handle. It involves re-partitioning the other disk, and modifying your /etc/fstab file -- either of which can create serious problems if anything goes wrong.

---

### Post by AvengerX9 on 2012-09-18
Thanks! I have allready emptied a big log file earlier this week, but right now there are no big files there anymore, but still Ubuntu is using about 30-35GB of the disk. The disk usage analyzer shows up and give me some details, but I'm not sure what to delete and how.

It says the 
/ is using 3.9GB
   usr is 2.5GB
   var is 639mb
   lib is 303mb
   home is 219mb
   opt is 119mb

---

### Post by JKyleOKC on 2012-09-18
That's a far cry from 30 GB, though. Have you emptied the trash folder (both your and that owned by root) recently? If you simply delete files from the GUI, they remain on the disk in a trash folder so you don't gain the space...

---

### Post by AvengerX9 on 2012-09-18
How can I delete the trash owned by root ?

---

### Post by JKyleOKC on 2012-09-18
You haven't said which version you are using so I'll have to be rather general instead of detailed. You need to open your file manager (Places) in super-user mode. The easiest way is to open a terminal window, then type "gksudo " followed by the name of your file manager program, which may be "nautilus" although in my system it's "thunar" since I'm using the XFCE window manager. A dialog will ask for your login password. Once you enter it, the file manager will open. You can then select "File System" to get the top-level screen of directories. Open "root" and type ctrl-h to display hidden files, one of which will be ".local" and inside that directory you should find "trash" which you can select. While it's selected, press and hold the shift key, then the delete key. That should do it...

In general, when you delete a file using "sudo" to gain permission to do so, it's moved into root's trash bin rather than your own. If you hold down the shift key while doing the delete, though, it will actually be deleted instead of going into a trash bin.

Hope this helps!

---

### Post by jrog on 2012-09-18
When it comes to moving /var/www to another hard drive, we need more information to tell you specifics. What is the device name of the other hard drive (e.g., /dev/sdb)? How is the drive currently partitioned, if at all (you can typically determine this by typing "sudo fdisk -l <device name>" at the command line, without the quotes and with the appropriate device name substituted for "<device name>")? Answering those two questions would be a start. :)

---

### Post by AvengerX9 on 2012-09-18
> **JKyleOKC said:**
> You haven't said which version you are using so I'll have to be rather general instead of detailed. You need to open your file manager (Places) in super-user mode. The easiest way is to open a terminal window, then type "gksudo " followed by the name of your file manager program, which may be "nautilus" although in my system it's "thunar" since I'm using the XFCE window manager. A dialog will ask for your login password. Once you enter it, the file manager will open. You can then select "File System" to get the top-level screen of directories. Open "root" and type ctrl-h to display hidden files, one of which will be ".local" and inside that directory you should find "trash" which you can select. While it's selected, press and hold the shift key, then the delete key. That should do it...

In general, when you delete a file using "sudo" to gain permission to do so, it's moved into root's trash bin rather than your own. If you hold down the shift key while doing the delete, though, it will actually be deleted instead of going into a trash bin.

Hope this helps!

I deleted the "trash" dir and I got like 28GB back it seems :) Thanks! ;)

How can I find the details about my 2nd drive ? :)

---

### Post by JKyleOKC on 2012-09-18
Use the commands that jrog gave a couple of messages back.

---

### Post by AvengerX9 on 2012-09-21
> **jrog said:**
> When it comes to moving /var/www to another hard drive, we need more information to tell you specifics. What is the device name of the other hard drive (e.g., /dev/sdb)? How is the drive currently partitioned, if at all (you can typically determine this by typing "sudo fdisk -l <device name>" at the command line, without the quotes and with the appropriate device name substituted for "<device name>")? Answering those two questions would be a start. :)



I get this

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ba9f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    69855231    34926592   83  Linux
/dev/sda2        69857278    78241791     4192257    5  Extended
/dev/sda5        69857280    78241791     4192256   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ac6adf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   488394751   244093952    7  HPFS/NTFS/exFAT

---

### Post by jrog on 2012-09-21
> **AvengerX9 said:**
> I get this

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ba9f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    69855231    34926592   83  Linux
/dev/sda2        69857278    78241791     4192257    5  Extended
/dev/sda5        69857280    78241791     4192256   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2ac6adf8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sdb2          206848   488394751   244093952    7  HPFS/NTFS/exFAT
Do you have anything on /dev/sdb right now?

---

### Post by AvengerX9 on 2012-09-22
No, its empty

---

### Post by jrog on 2012-09-22
> **AvengerX9 said:**
> No, its empty
Okay, good. Next question: it has two partitions on it (/dev/sdb1 and /dev/sdb2). Is that how you want it set up? If so, which partition do you want to use for /var/www? If not, how do you want to have the drive partitioned (e.g., just one partition for the whole drive, or more separate partitions, etc.)?

I think these should be the last questions before we can get to moving /var/www to that drive.

---

### Post by AvengerX9 on 2012-09-22
I was thinking of just having one partion. What do you think ?

---

### Post by jrog on 2012-09-22
> **AvengerX9 said:**
> I was thinking of just having one partion. What do you think ?
One is fine, but it partly depends on how large you think /var/www may get. If you want to go ahead and dedicate the full 250 GB to it, that's fine.

---

### Post by AvengerX9 on 2012-09-22
Yeah I wanna do that

---

### Post by jrog on 2012-09-22
> **AvengerX9 said:**
> Yeah I wanna do that
Okay, here are the steps. It's a long-ish process. Be forewarned that if something goes wrong here, there is a possibility of losing data; be as careful as possible.

1. First, go ahead and make sure the drive is currently unmounted by typing:

```
sudo umount /dev/sdb2 && sudo umount /dev/sdb1
```It might tell you it's already not mounted. That's fine.

2. Next, partition the drive appropriately by entering:

```
sudo fdisk /dev/sdb
```This will start up fdisk, for partitioning the drive. You can type 'm' to see your options, if you'd like. Otherwise, you can just do the following:

a. Type 'd' to delete a partition, and when it asks you for the number, type '2'.
b. Again, type 'd' to delete a partition; this time it shouldn't ask you for a number, since there is only one partition left. (If it does, though, type '1'.)
c. Type 'n' to add a new partition. Type 'p' for primary. Type '1' for the number. When it asks about the First Sector and the Last Sector, just hit enter (this will use the whole drive for one partition). 
d. Type 'p' to print the partition table. Verify that there is one partition, labeled /dev/sdb1, with the word "Linux" under the "System" column. (If it doesn't say "Linux" under "System", then do this: type 't', then type '83'.)
e. Type 'w' to write the partition table to the disk and exit fdisk.

3. Now you need to format the drive. You should probably choose either the ext3 or the ext4 filesystems (ext4 is newer but better performance-wise; ext3 is older and so perhaps more stable). Depending on what you choose, type **one** of the following two commands.

For ext3:

```
sudo mkfs.ext3 /dev/sdb1
```For ext4:

```
sudo mkfs.ext4 /dev/sdb1
```Wait for this to finish, then move to the next step.

4. Now you should temporarily mount the new partition so that you can move everything from /var/www onto it. Go ahead and do this like so:

```
sudo mkdir /newpart
sudo mount -t auto /dev/sdb1 /newpart
```5. Next, copy everything from your current /var/www to /newpart. The best way to do this is with the following commands (be sure to type them carefully):

```
cd /var/www
sudo sh -c "find . -depth -print0 | cpio --null --sparse -pvd /newpart/"
```6. Now we need to get rid of the current /var/www and replace it with the new partition on the other drive. We're not going to just delete /var/www yet, because we want to be safe; we'll just move it for now. Here's how to do all of this.

Move /var/www: 

```
cd
sudo mkdir /old
sudo mv /var/www /old
```Replace /var/www with the new partition on the other drive:

```
sudo mkdir /var/www
sudo umount /dev/sdb1
sudo mount -t auto /dev/sdb1 /var/www
```7. At this point, the new drive/partition should be mounted at /var/www, and all of the files that were previously in /var/www should be in place on the new drive. You need to verify this by browsing around /var/www and making sure everything is there. **If something is wrong at this point, stop everything you're doing and let us know.** Otherwise, continue.

8. Next, you need to tell your system to use the new drive/partition for /var/www permanently. (What you've done so far will only have it there temporarily.) First, backup your /etc/fstab file (this is where automounting parameters are specified):

```
sudo cp /etc/fstab /etc/fstab_backup
```Then, open the /etc/fstab file for editing in the editor of your choice. If you want to use gedit, for example, type:

```
gksudo gedit /etc/fstab
```If you want to use nano, for example, type:

```
sudo nano /etc/fstab
```Once it opens, create a new line at the end of the file that looks like this (replace 'ext3' with 'ext4' if that is the filesystem you chose to use earlier with mkfs):

```
/dev/sdb1 /var/www ext3 nodev,nosuid 0 2
```Be sure to type that correctly. This tells the system to always mount /dev/sdb1 at /var/www.

9. Reboot and make sure everything is working. Check to make sure /var/www is mounted on the new drive (you can check this by typing "mount" and looking for a line that begins with "/dev/sdb1 on /var/www"). Check to make sure that your files are all in place under /var/www. If so, move on. If not, let us know.

10. Everything should be set up at this point, so now you can clean up stuff you don't need. You can get rid of the /newpart directory you created, as well as the **old** copy of /var/www that is now under the /old directory. Be very careful with these commands, as a typo could result in catastrophic data loss:

```
sudo rm -rf /old
sudo rm -rf /newpart
```If you don't want your backup of your old /etc/fstab file, you can delete it, too:

```
sudo rm /etc/fstab_backup
```If you made it this far, congratulations; you now have your system set up as you wanted!

---

### Post by AvengerX9 on 2012-09-22
Okay, I did it until step #9 where I rebooted and I get a message saying "an error occured while mounting /var/www. Press S to skip mountin or M for manual recovery"

BTW, the new line I added, should that be ext3. I mean is it related to the ext3 and ext4 filesystems?

---

### Post by AvengerX9 on 2012-09-22
Hmmm, I changed from ext3 to ext4 in the file edit and it seems to work :) Thank you so much for the tutorial, it works great :)

---

### Post by jrog on 2012-09-22
> **AvengerX9 said:**
> Hmmm, I changed from ext3 to ext4 in the file edit and it seems to work :) Thank you so much for the tutorial, it works great :)
You're right, I meant to say that you should put in either 'ext3' or 'ext4' for the filesystem, depending on what you had selected earlier. I'll fix this in the original tutorial, in case anyone else reads it.

Glad it worked out!

Can you please mark the thread as solved (using the "Thread Tools" toward the top of the page) in case anyone else ends up searching for this material? Thanks!

---

### Post by AvengerX9 on 2012-09-22
Sure, I will mark it as resolved. Thanks again :)

---

