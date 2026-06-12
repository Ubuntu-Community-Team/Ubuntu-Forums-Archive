---
title: "PS3 hard disk upgrade using dd and gparted"
date: 2010-10-17
forum: Gaming &amp; Leisure
---

### Post by oly on 2010-10-17
to backup your ps3 hard disk to your laptop i removed the hard disk from the ps3 and placed it in a 2.5 inch hard disk bay and ran the command below, make sure you change /dev/sdb to be the correct disk your backing up, this create an exact copy of the disk you can restore from.


```
dd if=/dev/sdb conv=sync,noerror bs=64k of=~/Desktop/ps3.img
```

I then ran the below command to copy the image of the old drive onto the new disk, this will copy it on exact so if its a larger drive you will not get the extra space( but see below on how to rectify this), also make sure you choose the correct drive again and dont wipe out the hard disk with ubuntu on.

```
dd of=/dev/sdb conv=sync,noerror bs=64k if=~/Desktop/ps3.img
```

If you want the extra space you can format your old hard disk from the ps3 as fat32 (use gparted and make sure its fat32 ) windows and the ubuntu disk utility format as exfat which the playstation will not pick up.

Once you have formatted the disk attach the hard disk bay to your ps3 and backup and restore using the utility in the system settings menu this will give you all the space for your disk, and avoids needing a 3rd disk to backup because you used you desktop as the 3rd disk. :)

Hope this is useful for someone could not find any info on doing this in linux on the web so thought i would post it here for others reference.

---

### Post by briansage on 2010-10-21
Wow, you posted this only 4 days ago? Thank you, thank you, UForums, and thank you, Google. This was exactly the help I needed.

---

### Post by XP1 on 2011-01-05
**TL;DR**: The "Add New Disk" option in Acronis will corrupt the PS3 file system. Don't use Acronis or BackTrack to perform an image backup of a PS3 hard drive. Use a Ubuntu live disc. Perform a PS3 Utility Backup before attempting an image backup.

I have a PS3 that comes with a 40GB Seagate hard drive by default. Now, I want to upgrade the hard drive to a 500GB Seagate hard drive.

1) First Try: Acronis

At first, I tried to use Acronis True Image 2011 to create an image backup of the PS3 hard drive.

In the "My Disks" list, it just shows:
```
Disk 1
The disk is empty.
```

You can't select any checkboxes for the hard drive, which means that you can't click "Next". In fact, Acronis won't allow you to backup at all because there are no recognizable partitions on the drive. In this case, I can't even select a sector-by-sector backup.

Because I thought that the hard drive wasn't showing up, maybe I should try "Add New Disk" in Acronis. **[COLOR="Red"]WRONG! Do not try this.[/COLOR]** This "Add New Disk" option modifies or re-partitions the drive, which corrupts the PS3 file system.

Of course, I didn't know this at the time, so I proceeded anyway.
Because Acronis didn't work, I moved onwards.

2) Second Try: BackTrack

I searched the web for solutions to create an image backup of the PS3 hard drive. I read about dd, so I booted BackTrack 4 R2.

In Konsole, I couldn't see the PS3 hard drive, which was connected to the motherboard's SATA port. Next, I tried a SATA-to-USB cable / device, but that didn't work either.

3) Third Try: Ubuntu

I used a Ubuntu 10.10 64-bit Live DVD.

First, I had the PS3 hard drive connected directly to the motherboard's SATA port, but I couldn't find the hard drive listed in "sudo fdisk -l", "df", or "ls /dev". Then, I tried the SATA-to-USB cable / device, and it works and shows up as "/dev/sde", the path of which I initially confirmed in System > Administration > Disk Utility.

From there, I finished the two commands from this thread's original post. I had saved the PS3 hard drive IMG dump to an external hard drive.

Finally, I put the hard drive back into the PS3, and it shows this:
> The system software cannot be run correctly. Press the PS button to try to restart the system.

If the system cannot be restarted, the system partition of the hard disk must be reformated and you must reinstall the system software.
Connect storage media that contains update data of version 3.55 or later, and then press the START and SELECT buttons at the same time.
For information on how to obtain update data, refer to the SCE Web site for your region.

I had to re-install the 3.55 firmware onto the new 500GB hard drive. Once I did that, I did some testing to find out the cause of the problem.

It was actually the "Add New Disk" option that corrupted the PS3 hard drive.

In Ubuntu, I had unknowingly backed up the corrupted file system on the PS3 hard drive. Unless I can "un-corrupt" the backup, I have lost all of the existing data on my PS3 hard drive, and I have to start over fresh with a new 3.55 firmware install on the 500GB hard drive.

**Add this to everyone's advice: perform a PS3 Utility Backup before you try anything.**

---

### Post by XP1 on 2011-01-05
Thank you for your informative and helpful post.

> **oly said:**
> If you want the extra space you can format your old hard disk from the ps3 as fat32 (use gparted and make sure its fat32 ) windows and the ubuntu disk utility format as exfat which the playstation will not pick up.However, I am ultra confused on this step. Why is it necessary to format as FAT32 and then format exFAT over it? Why not just format as exFAT?

And what? Ubuntu has exFAT support? I'm surprised.

How does this step work? If you insert an exFAT hard drive into the PS3 and launch the Backup / Restore Utility, the PS3 hard drive will magically recognize the extra space on the newly installed hard drive?

---

### Post by owenstokes on 2011-02-02
I get the following error when using dd to restore the drive (yes it's the same drive - was reformatted by Sony repair center and yes the original dd to create the image file completed error free).

dd: writing `/dev/sdc': No space left on device
1221106+0 records in
1221105+0 records out
80026361856 bytes (80 GB) copied, 2810.26 s, 28.5 MB/s

Do I need to 'prep' the disk before running the second dd to restore the drive?

The bytes transfered are 40957 LESS than the image file.  PS3 won't recognize the drive.

Please help!  Thanks.

---

### Post by mips on 2011-02-03
> **owenstokes said:**
> I get the following error when using dd to restore the drive (yes it's the same drive - was reformatted by Sony repair center and yes the original dd to create the image file completed error free).

dd: writing `/dev/sdc': No space left on device
1221106+0 records in
1221105+0 records out
80026361856 bytes (80 GB) copied, 2810.26 s, 28.5 MB/s

Do I need to 'prep' the disk before running the second dd to restore the drive?

The bytes transfered are 40957 LESS than the image file.  PS3 won't recognize the drive.

Please help!  Thanks.

The disk is probably slightly smaller. I have two 500GB drives but the one is slightly smaller than the other so the image won't fit. You could try and do a Secure Erase on the disk with hdparm that will free up a bit of space on the drive. Alternatively resize the original partition slightly and just image the partition and not the drive.

---

### Post by owenstokes on 2011-02-27
I got a 120GB drive, restored the 80Gb image to it via the dd command described above and the Playstation come up with: The disk must be formatted.

What am I missing?

---

### Post by user024 on 2012-02-17
I did the exact same thing, following the steps above, with success. (Copying the PS3 HDD to a bigger one).
There is only one thing that is missing in the first post. The author assumes that we only have one sata HDD other than the PS3 one we connect via the hard disk bay connected to our system.
Since the author followed the procedure with a laptop, that was most likely the case.

Yet, if your system has other hard disk drives attached to it, or/and maybe USB drives, the PS3 HDD could be sdb, sdc, and so on...
So owenstokes, who has probably formatted his 120GB drive, since it's almost a year since he had that problem already, possibly copied and rewrote another drive attached to his computer.

A good way to find out the name of the drive you attached is to use the "Disk Utility" from your System>Administration programs, and find out the one drive witch fits the dercription of your personal PS3 HDD. One clue (other than the capacity) will be that the file system won't be known to your Ubuntu computer.

So if your PS3 HDD is, say, sd[COLOR=DarkRed]x[/COLOR], the first command would be:

```
dd if=/dev/sd[COLOR=DarkRed]x[/COLOR] conv=sync,noerror bs=64k of=~/Desktop/ps3.img
```

And if the new HDD is sd[COLOR=DarkRed]y[/COLOR], the second command would be:

```
dd of=/dev/sd[COLOR=DarkRed]y[/COLOR] conv=sync,noerror bs=64k if=~/Desktop/ps3.img
```

while it might as well be named with the same last letter as the original drive.

Also, the above commands should probably need root privileges to do the work.
I know they needed "sudo" in my case.

I hope that all this was kind of helpful. The thread, certainly was for me.
:D

---

### Post by Zanz on 2012-03-02
Hi

I tried to copy my ps3 harddrive, but i always get an errror message which says permission denied. 

I just entered the command at the terminal. The Harddrive is shown in the app disk utility.

I really need help, cause my ps3 is broken and can't be repaired so in order to use my harddrive in my new ps3 i have to format it :-/

thanks

---

### Post by Zanz on 2012-03-02
Hi 

Its me again :-)

ok the copy process is working but very slow and i have error and input errors. at the beginning i had 3 mb/s and now i have just 870kb/s

see picture

is it ok to have error messages due to the coding of the ps3 system? is there a possibility to increase the speed?

thank[  Unbenannt.PNG]("http://ubuntuforums.org/attachment.php?attachmentid=213605&stc=1&d=1330719910")

---

### Post by PCFreak2 on 2012-03-04
Or you could just back everything up to an external with the PS3's backup utility
Replace Internal inside PS3
Boot safe mode and run options 2-5
Reboot
Restore PS3 backup from external

This is the preferred method from Sony......

---

### Post by BRTPOB on 2012-05-21
Unless of course the backup utility continually tells you "The USB device cannot be accessed." then you can't use the Sony Backup Tool and something like this is the perfect solution to an otherwise incurable scenario.

---

