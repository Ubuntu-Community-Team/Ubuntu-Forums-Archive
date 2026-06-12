---
title: "Retrieving files from other operating system"
date: 2009-03-24
forum: General Help
---

### Post by baker126 on 2009-03-24
Sorry if this is an extremely noob question...

I set up a dual partition on my hard drive some time back; one for Windows XP and the second for Fedora 10.  I have been wanting to try Ubuntu for awhile so last night, I set up a third partition and installed Ubuntu.  

The boot loader configured to start Ubuntu by default...obviously...and Windows XP as the other.  There is no listing for Fedora, which really does not bother me.  My problem is I need to access some files in the Fedora partition, but it does not show up anywhere!  I can mount the local NTFS disk, but the partition with Fedora is not showing up.

Is there anyway to retrieve the files from Fedora?

Remember, I am a noob, so dumb down your responses.

---

### Post by James_Lochhead on 2009-03-24
You need to find out which partition your fedora root or fedora home (if you have a separate home partition is. Use this command in the terminal:

(You might need to try hda instead)

```

sudo fdisk -l /dev/sda

```

Output for me looks like this:

```

james@james-laptop:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x332b332a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  83  Linux
/dev/sda2              25       38913   312375892+  83  Linux
james@james-laptop:~$ 

```

You can work out roughly what size the partition is from the start and end numbers.

When you have figured it out you can then mount the partition:

Lets say for example fedora is sda2

```

sudo mkdir /media/MyFedora
sudo mount /dev/sda2 /media/MyFedora

```

Fedora should be mounted to /media/MyFedora

---

### Post by Coreigh on 2009-03-24
actually you can leave the /dev/sda part off and fdisk will show all partitions on all disks in the computer:
```
sudo fdisk -l
```

---

### Post by baker126 on 2009-03-24
Thanks for the prompt reply....I think I am getting there.

When I do the commands, I get an error.  There are seven partitions on my disk:

sda1 Dell Utility
sda2 NTFS
sda3 Linux
sda4 Extended
sda5 Linux LVM
sda6 Linux
sda7 Linux Swap

sda6 and 7 are for my Ubuntu.  I am assuming sda3, because it is so small, is the boot loader.  That would leave sda5 as my Fedora partition.  I made the directory and attempted to mount the partition when I get this error:

mount:  unknown file system type 'LVM2_member'

Just for fun, I changed the command to mount my Ubuntu partition in the Fedora folder and it worked fine....

And ideas?

---

### Post by James_Lochhead on 2009-03-24
The problem is the LVM bit.

I am not sure of the procedure for mounting volumes that are contained in LVM. Maybe someone more experienced can tell you.

An alternative would be simply to grab a fedora live cd, restore grub from fedora, mount the Ubuntu partition, transfer everything you want, grab an Ubuntu live cd and restore grub.

There is probably an easier (and less painful) way. You can probably mount volumes contained in LVM, but I have no idea how.

---

### Post by James_Lochhead on 2009-03-24
[http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html]("http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html")

Here is a link for mounting an LVM volume.

---

