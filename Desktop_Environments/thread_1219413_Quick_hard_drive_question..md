---
title: "Quick hard drive question."
date: 2009-07-21
forum: Desktop Environments
---

### Post by JJ1 on 2009-07-21
Quick question here, probably asked a thousand times, but. I have Ubuntu installed on an 80 Gig Sata Hdd. I recently picked up a 1 tb Sata hdd and hooked it up. Ubuntu sees it as a mass storage drive, and will not tell me how big it is Or mount it. Says unable to mount location. I ran the sudo fdisk -l Command, and got this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

```

I don't believe it is being recognized. If so, please tell me which one it is. If not, how can I format this drive to run with Ubuntu? As I said this hard drive is brand new, so I have no idea what format it's in/if it's ever been formated. Thanks for reading guys.

---

### Post by lukeiamyourfather on 2009-07-21
It looks like the drive is not detected since all of the items listed start with "sdb" which means the second drive, first or third drive would be "sda" and "sdc" followed by the partition number. Does GParted see the drive? Not sure if not partitioned disks show up in fdisk or not. Cheers!

---

### Post by SuperSonic4 on 2009-07-21
Chances are it has not been formatted, what happens if you try and look it up in gparted

---

### Post by tcturner on 2009-07-21
It's not recognizing the drive. Here is my sudo fdisk -l Command :

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00055f28

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9480    76148068+  83  Linux
/dev/sda2            9481        9729     2000092+   5  Extended
/dev/sda5            9481        9729     2000061   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002a222

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux

 I have an 80 Gb with ubuntu installed on sda1 as / (root). sda2 sda5 (same partition) is a 2 Gb swap. Almost exactly what you have but yours is labeled sdb. This could be because of your jumper settings on your hard drives. My 80  Gb jumper is set to master. The 40 Gb jumper is set to slave. Also the 40 Gb is formatted with ext3. Once you partition and format the 1 Tb it should show up in Places-Computer as 1 Tb media or something along those lines.

---

### Post by JJ1 on 2009-07-21
Thanks for the help thus far. How do I install, or open Gparted?

Edit: Also, Tcturner, you are using IDE?

---

### Post by nexus_2006 on 2009-07-21
To install gparted (which is one of my favorite utilities ever, btw) just look for it in Synaptic or type

"sudo apt-get install gparted"

type "sudo gparted" to run it.  Very intuitive, use the drop menu in the upper right to select different devices like your new HDD.

---

### Post by JJ1 on 2009-07-21
> **nexus_2006 said:**
> To install gparted (which is one of my favorite utilities ever, btw) just look for it in Synaptic or type

"sudo apt-get install gparted"

type "sudo gparted" to run it.  Very intuitive, use the drop menu in the upper right to select different devices like your new HDD.

Fantastic thank you sir. Not quite 1 tb, but I know this isn't my 80 gig hdd =P

[IMG]http://img.photobucket.com/albums/v728/demond349/Screenshot-7.png[/IMG]

Next what? Also, can I make it see the full tb?

---

### Post by nexus_2006 on 2009-07-21
Probably won't be able to use it all.  I forget why, but its something like the difference between the number used to advertise and real useful capacity.  HDDs have more or less always been like this (I'll bet you can only use 70 some GB of your 80 GB drive), but the effect is more pronounced with larger and larger drives.  Now select that grey area, and make a parititon in it (either the whole thing or several smaller partitions that add up to the total drive capacity), and format them.  EXT3 is what I personally recommend, but you have lots of choices like EXT4, REISERFS, or even a Windows compatible file system like the older FAT32 or NTFS.  Then, you can use the space.

---

### Post by JJ1 on 2009-07-21
Just a slave drive so I just need 1 partition I believe. Here is my options:

MsDos
Aix
amiga
Bsd
Dvh
Gpt
Mac
Pc98
Sun
Loop

Which do I want? And is there anything special I have to do to get it only 1 partition?

Thanks muchly for your help by the way.

---

### Post by nexus_2006 on 2009-07-21
Just click the unpartitioned space, then hit "new" on the toolbar.  Select the size you want with the number boxes or the slider graphic, then the pull down menu labeled file system should have choices like EXT2, 3, 4; REISERFS, FAT32, etc.

---

### Post by JJ1 on 2009-07-21
> **nexus_2006 said:**
> Just click the unpartitioned space, then hit "new" on the toolbar.  Select the size you want with the number boxes or the slider graphic, then the pull down menu labeled file system should have choices like EXT2, 3, 4; REISERFS, FAT32, etc.

I don't get those options. I click New, and it says:

Warning, will erase all ect.

Then a drop down box with only the options I listed above, Then 2 buttons. Create, or cancel. If I clock create, will it take me into more options? And also, I'm sure I don't want it in Msdos, which should I choose?

---

### Post by nexus_2006 on 2009-07-21
Hmmmm, now you've stumped me, I don't get anything like that.  Might as well play around with it, provided you have the new and presumably empty drive selected I can't imagine anything getting hurt.  Or you could try some of the terminal-based partitioner/formatters.

---

### Post by JJ1 on 2009-07-21
> **nexus_2006 said:**
> Hmmmm, now you've stumped me, I don't get anything like that.  Might as well play around with it, provided you have the new and presumably empty drive selected I can't imagine anything getting hurt.  Or you could try some of the terminal-based partitioner/formatters.

Which format should I try it in?

---

### Post by theozzlives on 2009-07-21
Probably NTFS, ext3, or ext4. Go back to your GUI and access gparted by going: System, Administration, Partition Editor.

---

### Post by JJ1 on 2009-07-21
> **theozzlives said:**
> Probably NTFS, ext3, or ext4

I listed all of the format options I have, which is none of those. The only one I see I am familiar with is MSDos, but I need this formatted for Ubuntu storage.

---

### Post by lukeiamyourfather on 2009-07-21
That's probably the partition type its asking for. The default is MS DOS which is fine. Then format the partition as EXT3 (recommended), or whatever file system you'd like to use. Cheers!

---

### Post by JJ1 on 2009-07-21
> **lukeiamyourfather said:**
> That's probably the partition type its asking for. The default is MS DOS which is fine. Then format the partition as EXT3 (recommended), or whatever file system you'd like to use. Cheers!

You sir are a mastermind (:< I think it's working, will keep updated.

---

### Post by JJ1 on 2009-07-21
> **JJ1 said:**
> You sir are a mastermind (:< I think it's working, will keep updated.

Alright I partitioned it with one partition, and it was successful. But for some odd reason, it used 14 gigs to do so, and it disapeared from the computers list, as it does not recognize it as a file system or storage device now. It is now located in the filesystems folder. Any suggestions?

---

### Post by JJ1 on 2009-07-21
> **JJ1 said:**
> Alright I partitioned it with one partition, and it was successful. But for some odd reason, it used 14 gigs to do so, and it disapeared from the computers list, as it does not recognize it as a file system or storage device now. It is now located in the filesystems folder. Any suggestions?

Some screenshots:

[IMG]http://img.photobucket.com/albums/v728/demond349/Screenshot-8.png[/IMG]

[IMG]http://img.photobucket.com/albums/v728/demond349/Screenshot1-1.png[/IMG]

[IMG]http://img.photobucket.com/albums/v728/demond349/Screenshot3.png[/IMG]

[IMG]http://img.photobucket.com/albums/v728/demond349/Screenshot4.png[/IMG]

[IMG]http://img.photobucket.com/albums/v728/demond349/Screenshot5.png[/IMG]

---

### Post by lukeiamyourfather on 2009-07-21
I'm not really following what that is? Take the UUID from the new drive (get it from GParted) and use that in the /etc/fstab to mount the drive at boot time. Traditionally media gets mounted through /mnt/* but you can mount it somewhere else if you want. Must use sudo to edit /etc/fstab and there are directions there for adding another drive. Using defaults for the options should be fine. Cheers!

EDIT: Right click a partition and selection information when in GParted to get the UUID of a drive. Example line of /etc/fstab looks like this.

```
UUID=84b3ad4a-d04c-4366-b78c-62901d1197c2     /mnt/scenes     ext3     defaults     0     3
```

The /mnt/scenes is where the drive gets mounted. The "ext3" is the format of the drive, and defaults is what options (read, write, etc.), and the last two are for the error checking of the drives. Don't remember the second to last column, last column is what order to check disks in. Cheers!

---

