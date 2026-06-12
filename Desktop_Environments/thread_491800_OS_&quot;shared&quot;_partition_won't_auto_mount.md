---
title: "OS &quot;shared&quot; partition won't auto mount"
date: 2007-07-04
forum: Desktop Environments
---

### Post by mtbsoft on 2007-07-04
Hi

I recently got a new Dell laptop with XP installed and thought it the ideal opportunity to try Linux (at long last).  I followed [this excellent guide]("http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/") and successfully dual booted XP and Ubuntu.  After a week of trialling it I decided to do a total reinstall (though again dual-boot, I have my reasons) in order to get rid of all the Dell junk and other issues.  

The rebuild all went just fine but I've noticed one niggling little thing.  After the first install, both the XP volume and the "OS Share" fat32 volume were automatically mounted at startup/login, however this time the "OS Share" volume doesn't automatically mount.  The only key difference between the installs I can think of is that this time the fat32 partition is much larger than before and the XP partition is smaller;  the number of partitions on the drive is lower but I've still used the same types as before.

I can mount the fat32 volume manually, simply by clicking the Computer button in the File Browser, then right-clicking the drive in the list and selecting Mount Volume. However, as I regularly need to access the data on this volume(from both XP and Ubuntu) I would like it to automatically mount.

I've searched around for various solutions and checked the /etc/fstab file - I've checked man for the mount command but couldn't see anything obviously wrong. I've tried a few changes both in fstab and in the properties dialog of the volume - but just can't see why the volume isn't mounting itself.

Can anyone suggest anything to point me in the right direction on this, please...!

---

### Post by Analord on 2007-07-04
Yes i can.

Edit your /etc/fstab with sudo 
Here is my line for vfat (fat32) partition.
# /dev/hda3
 /media/hda3     vfat    umask=077,uid=1000


Just change your accord. to your partition names, numbers and UID
you can view your uid by editing your /etc/passwd file and check out the number next to user you are using.

---

### Post by mtbsoft on 2007-07-04
Thanks for your reply mate but no joy I'm afraid.  

I've tried all sorts of variations of what you showed me and they all point blank refuses to auto mount, even renamed the share in XP (as I noticed the name was carried over) in case it had some persistance associated with it.  I also tried creating a matching mount point in /media (according to something I saw in another thread) but that seems to make no difference either.

I'm happy to blow the fat32 partition away and recreate it again but, since I tried that once before, I don't hold much hope.  Are there any special options I should set when creating the partition that I could have missed?

---

### Post by mtbsoft on 2007-07-08
Finally solved this!  I eventually deleted the partition, then recreated it according to [this]("http://ubuntuforums.org/showthread.php?p=2984243") thread using new names I hadn't before, then finally amended the fstab entry according to your guidelines.  

A good joint effort with excellent results.

Thanks again.

---

