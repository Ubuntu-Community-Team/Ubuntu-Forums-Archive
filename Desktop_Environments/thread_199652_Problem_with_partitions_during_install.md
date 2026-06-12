---
title: "Problem with partitions during install"
date: 2006-06-19
forum: Desktop Environments
---

### Post by ralphiekabo on 2006-06-19
Hello,

I'm completely new to the Linux world. I thought I would give Ubuntu a shot, and installed it on my computer. However during install it installed all of Ubuntu into a new partition I'm sure I didn't create, leaving me with 40mb free space.
I already have 2 partitions, both approximatley 40 gig. One holds Windows, and I was trying to install Ubuntu on the other. That obviously didn't work, and as I don't know anything about Ubuntu I urgently need some help in joining the empty partition to the one Ubuntu is in, or something of the sort.

---

### Post by Luke771 on 2006-06-19
Format the free space you have as fat32 to get a file storage partition accessible by both OSes
Windows doesnt read Ext2 (ext3, reiserfs) and you don't want to write on a NTFS partition with linux (that can screw up the drive) so having a FAT32 partition as well is actually smart.

You can use Qparted to actually create the partition on your free space, you can install that from the repositories using Synaptic.
Then you'll need to add the new partition to fstab
```

sudo mkdir /media/hda6
sudo gedit /etc/fstab

add the line:
/dev/hda6       /media/hda6      vfat    defaults,nls=utf8,umask=007,gid=46 0       1
```
the first line creates your mount point, a directory called 'hda6' in the /media directory
the second line opens /etc/fstab in 'super user mode'

the third line is the one you add in /etc/fstab to automatically mount your new partition at startup,
in that line:
The first term from the left (in our line '/dev/hda6') is the location of the device
the second one (/media/hda6) is the mount point
The third term is the file system (fat and fat32 are both called 'vfat' in linux)


Note: I'm assuming that your new FAT32 partition is the second logical partition created: the two OS partitions should be primary and the swap space can be logical so that would be the first logical partition (that's always a 5) so the new fat 32 partition will be hda5.

---

### Post by cotcot on 2006-06-19
If I understand you well you want to merge the new 40 GB partition with Ubuntu on and the empty partition of 40GB to 1 partition of 80 GB ?

Then I suggest to backup what you might not loose first an then to delete the empty partition. You can used Gparted, QTParted, parted or fdisk to do that. Make sure that the empty partition is not mounted.

The less obvious part is to move the ubuntu partition to fill the gap between the windows and ubuntu partition. This is to be done in terminal using 'parted'. Please take some time to read the GNU Parted manual : [http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC20]("http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC20") 
Afterwards you can resize the ubuntu partition to whatever size you want using Gparted, QTParted, parted.

---

