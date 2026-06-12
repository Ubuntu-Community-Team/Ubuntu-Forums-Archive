---
title: "Ubuntu Installation error"
date: 2006-02-26
forum: Desktop Environments
---

### Post by cjg on 2006-02-26
My first attempt to install Ubuntu.
Default clean installtion, ie only Ubuntu.
No network.
Error Message
Base system installation error
Base system installation into \target\ failed
Failing step "Install the base system"

Any ideas?

Intel Celeron Processor
Seagate ST310230A 10GB IDE Hard Disk
Memory 42958K

thx

cjg

---

### Post by GreyFox503 on 2006-02-26
You may want to first confirm that the CD you are using is good.  If you downloaded & burned it, then you can check the MD5sum of the *.iso file against [these ones]("http://mirror.mcs.anl.gov/pub/ubuntu-iso/5.10/MD5SUMS").  There are free programs for Windows and Linux to check this for you, like [this one]("http://www.md5summer.org/").  If your result is the same as the one on the website, then your download went correctly.  If it is at all different, that means there was an error in the download.

Also, try burning the CD at a low speed like 8x or 4x.  This will reduce the chance of errors.

If you have done both of these things and you still cannot install, then you may have a more serious problem.


EDIT:  42958K of RAM?  That's a lotta memory.  :)

---

### Post by cjg on 2006-02-26
It is not a download >>>> I used the Ubuntu CD version 5.10 that I requested through shipit.ubuntu.com. (Recieved 5 copies)

Sorry the memory is 425984K; lotsa memory is good for speed if you use windows!

---

### Post by GreyFox503 on 2006-02-26
Can you give us more info about the partitioning scheme, how things are set up?  A 10 GB drive is just the right size to devote to Ubuntu.  I don't know what you did, but the partitioner does a pretty good job at automatically dividing your hard drive.

Was there anything on the disk before you installed?  How much space did you give the / partition, etc.

---

### Post by cjg on 2006-02-27
The disk was previously used for a windows installation.
During setup of Ubuntu
At startup I used the default option by pressing Enter
No Network 
When asked what type of format I specified the whole disk as one partition.
The program allows 3 options I tried both that does the job automatically, I did not try the one where the
I tried 
Erase entire disk
and then I started over and tried
Erase entire disk and use LVM

and then it ended with the messages mentioned in my first thread.

---

### Post by GreyFox503 on 2006-02-27
Ok, here's what I would do.  Pop in your Ubuntu CD and start the installer again.  Don't worry about the networking part.  After entering the hostname, you will see the partitioner again.

1)  Select "Manually edit partition table"

2)  Go down to the list of hard drives.  If you have more than one hard drive in your system, make sure you're working with the 10GB one that you want Ubuntu on.

3)  Press enter on the line that says something like IDE1 master (hda) - 10.0 GB.  Except it might not be IDE1 master, it may be something else.  Just make sure you pick the drive that you're installing Ubuntu on.

4)  It will ask you "Create new empty partition table on this device?"  Doing this action will erase EVERYTHING on the disk you selected, so be sure about it.  Press yes to create a new partition table.

5)  Now, underneath that drive, you should see only one line that looks something like this:
```

         pri/log     10.0 GB       FREE SPACE
``` 
It should be the same size as the drive above it.  Select this new line that says "FREE SPACE."

6)  Select "Automatically partition the free space."

7)  Now you should go back to that screen, and see two lines under the hard disk. 
One will say                       .  .    .   . . . . . .primary.... ext3....   /
And the other will say          .  . logical....... swap..... swap

It will give most of the drive (probably around 9 GB) to the / partition, and probably less than 1 GB to the swap partition.  As long as there is at least 4 or 5 GB for the / partition, that should be enough.

8)  Up to this point, no physical changes have actually been made to your disks.  Check to made sure you are satisfied with how things look.

9)  When you are ready to continue, press "Finish partitioning and write changes to disk".  It will ask you one last time to make sure you are ready with "Write the changes to disks?"  Select Yes to continue.  This will permanently alter the hard drives to make your changes, and it will continue installing the system.



Whew.  Hopefully this will set you straight.  If not, let us know.

---

### Post by cjg on 2006-02-27
[QUOTE=GreyFox503]Ok, here's what I would do.  Pop in your Ubuntu CD and start the installer again.  Don't worry about the networking part.  After entering the hostname, you will see the partitioner again.

1)  Select "Manually edit partition table"

2)  Go down to the list of hard drives.  If you have more than one hard drive in your system, make sure you're working with the 10GB one that you want Ubuntu on.

3)  Press enter on the line that says something like IDE1 master (hda) - 10.0 GB.  Except it might not be IDE1 master, it may be something else.  Just make sure you pick the drive that you're installing Ubuntu on.

4)  It will ask you "Create new empty partition table on this device?"  Doing this action will erase EVERYTHING on the disk you selected, so be sure about it.  Press yes to create a new partition table.

5)  Now, underneath that drive, you should see only one line that looks something like this:
```

         pri/log     10.0 GB       FREE SPACE
``` 
It should be the same size as the drive above it.  Select this new line that says "FREE SPACE."

6)  Select "Automatically partition the free space."

7)  Now you should go back to that screen, and see two lines under the hard disk. 
One will say                       .  .    .   . . . . . .primary.... ext3....   /
And the other will say          .  . logical....... swap..... swap

It will give most of the drive (probably around 9 GB) to the / partition, and probably less than 1 GB to the swap partition.  As long as there is at least 4 or 5 GB for the / partition, that should be enough.

8)  Up to this point, no physical changes have actually been made to your disks.  Check to made sure you are satisfied with how things look.

9)  When you are ready to continue, press "Finish partitioning and write changes to disk".  It will ask you one last time to make sure you are ready with "Write the changes to disks?"  Select Yes to continue.  This will permanently alter the hard drives to make your changes, and it will continue installing the system.



Whew.  Hopefully this will set you straight.  If not, let us know.[/QUOTE]
No luck
But I have a new error message

Unable to install initrd-tools
An error was returned while trying to install the initrd-tools package onto the target system.
 Chek /target/var/log/bootstrap.log for details

The failing step is : Install the base system (same as previously)

Regards
Johan

---

### Post by GreyFox503 on 2006-02-27
Hmm.  I'm stumped.  If you have a bootable CD, you could check /var/log/bootstrap.log to see what it says, but I doubt that will contain much info...

The install seems to be failing on some very basic level.  If you have enough space and the partitions are correct, that should be all you need.  If you haven't already, you could try using some of your other 5 discs you ordered to install from.  Other than that, I really can't think of much.  You have done everything correct as far as I can tell.

If you just can't get it to install, the only other course of action I have is to download another distro and see if it fares any better.  (You could check back in a couple months when Dapper's ready!)

Hopefully someone else will have some suggestions as for how to proceed.

---

