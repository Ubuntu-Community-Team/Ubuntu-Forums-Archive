---
title: "How do I format a second HDD?"
date: 2005-12-28
forum: General Help
---

### Post by andysdp on 2005-12-28
I have successfully installed breezy and been using for a few weeks, however my machine has two 80Gb HDD's and I need to format the slave.

Using system>admin>disks The two disks are present - /dev/hda looks all normal with the partitions as setup on installation.  /dev/hdc is listed - but no partitions. 

How do I format / partition this drive? Can't see any installed applications to do this. Is qparted an option (not that I have used this before!)

Thanks

Andy

---

### Post by Jammy_Stuff on 2005-12-28
I don't know how to format it to a linux file system, but you could get a Windows 98 boot disk and use fdisk to format it to FAT, then mount that.

---

### Post by zoiks on 2005-12-28
I see a "Create" button in the Partitions tab.  I also see a "Format" button.  Once the partition is created, I assume you can simply hit format, and choose a file system (ext3 or reiserfs are probably recommended).  If you don't like using the gui, you can use "sudo fdisk <drive device>" to create the partitions and "sudo mkfs -t <type> <partition>", for example "sudo mkfs -t reiserfs /dev/hdc1".  (Note I haven't used the gui, I just saw that the functionality seems to be there.)

---

### Post by andysdp on 2005-12-28
Thanks for your suggestions Zoiks. The "create" button in "disks manager" are greyed out. I suppose this has to run as root - but I don't know how?

The help doesn't work either!

Not confident with fdisk in the terminal - Any body know any tutorials on this?

---

### Post by andysdp on 2005-12-28
Downloaded GParted and have now partitioned my 2nd drive. Had to change the permissions for all users.  Piece of cake!!

---

### Post by Refrozen on 2005-12-28
[parted](http://manlib.com/man/296) or [fdisk](http://manlib.com/man/320) should be of assistance :)

---

### Post by sciurus on 2005-12-29
gparted or cfdisk.

---

### Post by ekravche on 2005-12-29
[QUOTE=sciurus]gparted or cfdisk.[/QUOTE]

didn't work for me. It said that I didn't have permissions to perform this operation. Here is the exact error:

Opened disk read-only - you have no permission to write

                       FATAL ERROR: Cannot get disk size
                          Press any key to exit cfdisk

[QUOTE=Refrozen]parted or fdisk should be of assistance :) [/QUOTE]
 

gave me this error:

You will not be able to write the partition table.

Unable to read /media/SANVOL

---

### Post by steve.horsley on 2005-12-30
[QUOTE=ekravche]didn't work for me. It said that I didn't have permissions to perform this operation. Here is the exact error:

Opened disk read-only - you have no permission to write

                       FATAL ERROR: Cannot get disk size
                          Press any key to exit cfdisk


 

gave me this error:

You will not be able to write the partition table.

Unable to read /media/SANVOL[/QUOTE]

Try **sudo cfdisk**. Repartitioning disks is something that only root is allowed to do.

---

