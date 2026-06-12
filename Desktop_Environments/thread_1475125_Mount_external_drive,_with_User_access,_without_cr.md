---
title: "Mount external drive, with User access, without creating mount point"
date: 2010-05-06
forum: Desktop Environments
---

### Post by inspired on 2010-05-06
Hi folks,
I have an external drive with two partitions on it. One is EXT3 and the other is NTFS.
When I plug it in (which I can do via USB or Firewire) the NTFS one mounts with full user access. But the other one mounts with only root access. Oddly (and I can't double check just now, but will later) I think both show ROOT as the owner, etc., in their permissions. I would have to double check that though.

I need the EXT3 partition to mount with full USER access. I know that I can set up an entry in fstab (as per [http://ubuntuforums.org/showthread.php?t=1119974](http://ubuntuforums.org/showthread.php?t=1119974)) but I understand this requires manually creating the mount point (e.g. /media/mounted_drive). This poses an issue for me. I use this drive partition purely for automated backups from my system. If I create a mount point manually it, obviously, stays there whether or not the drive is mounted or not. Then when the backup system runs it will think the drive is mounted and start loading files onto my local hard drive. Correct?

This was an issue I came across some years ago when I went through this very thing before... I had a device I was doing backups to, and when it was not plugged in my local HDD would get maxed out by the backup system backing up the whole system to my local drive.

Here is my million dollar question:
***Is there any way I can have this external HDD partition mount with full access to USER, not just ROOT... without creating the mount point manually?***

Thank you so much for your help.

Cheers,

Jonathan

---

