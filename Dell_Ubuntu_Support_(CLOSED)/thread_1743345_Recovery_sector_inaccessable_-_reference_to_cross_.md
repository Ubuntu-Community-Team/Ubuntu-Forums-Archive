---
title: "Recovery sector inaccessable - reference to cross post"
date: 2011-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 7eieio on 2011-04-29
My apologies for not looking more carefully and posting this in the more appropriate forum to begin with:

[http://ubuntuforums.org/showthread.php?p=10738987#post10738987](http://ubuntuforums.org/showthread.php?p=10738987#post10738987)

Allasso

---

### Post by gbrainin on 2011-04-29
First thing you should do is see if the recovery partition is still there.  You can use gparted for this.  If you don't see two non-Linux (FAT/NTFS) partitions (one for the Dell utility partition, one for the recovery), then your recovery partition has been erased somehow, and you're probably out of luck.

---

### Post by 7eieio on 2011-05-01
Yes, the recovery partition is there.  However, according to the Dell forum, installing grub probably erased the boot sector that is used to boot into the recovery partition.  They said that fdisk /MBR will not rewrite it either, as it is different from the master boot record used to boot Windows.

I wondered if by making the recovery partition bootable using fdisk or gparted, I could get it to show up on the grub menu.  However, when running fdisk, interestingly, the only partition marked bootable is the Windows partition.  So apparently my idea of what makes a partition bootable is in error.

As an aside, I would be interested in getting an image of the boot sector Dell was talking about, but that would sure be a long shot.

Thanks for the reply.

---

### Post by gbrainin on 2011-05-01
I was going to suggest trying to get it as an option on the grub menu.  I'm not sure you even need to have the partition marked as bootable for this to happen.  I'm not familiar with the procedure under the new version of grub, but I'm sure there is a way to reconfigure it to allow that partition as one of the boot options.

---

### Post by 7eieio on 2011-05-02
> **gbrainin said:**
> I was going to suggest trying to get it as an option on the grub menu.  I'm not sure you even need to have the partition marked as bootable for this to happen.  I'm not familiar with the procedure under the new version of grub, but I'm sure there is a way to reconfigure it to allow that partition as one of the boot options.

The (preferred) way to manually add an entry to the grub menu in grub2 is by editing the /etc/grub.d/40_custom file and running update-grub.  Some help on that subject can be found here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://linuxers.org/howto/how-configure-grub2-ubuntu-910](http://linuxers.org/howto/how-configure-grub2-ubuntu-910)

However, I was not successful for when I try to boot into what I believe is the restore partition, I get a "Can't load kernel file" message.  I wasn't sure if the code I put into the entry was correct, so after paring down another Dell entry (Dell Utility Partition), I found I was still able to boot into that partition with the minimal code:

set root=(hd0,x)
chainloader +1

But when using the same format to try to boot into the restore entry it fails.

Either I am in error about the partition I believe to be the restore partition, or there is something more I need to know about getting grub configured properly to do this.

---

