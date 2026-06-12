---
title: "Partition Problem"
date: 2009-06-23
forum: General Help
---

### Post by azigma on 2009-06-23
Installed Ubuntu wubi dual boot with winxp pro,but screwed up and wanted to start fresh so followed an uninstall procedure for Ubuntu listed on many places on internet.
Steps were to:
Restore MBR
Delete the partition
Resize windows partition

Did the restore, then went to Disk Management to delete the Ubuntu partition, trouble is all I see is my "C" drive, no indication of a Ubuntu part. (Still have the dual boot option present when I log in)
How do you delete it when you can't see it, is it present but hidden ?
Not an expert and I don't want to screw up the existing windows installation, your help would be appreciated.

---

### Post by hibliss on 2009-06-23
I am confused. You used Wubi, so there was no partition to delete. Wubi is removed through Windows add/remove programs.

---

### Post by nice_like_rice on 2009-06-23
Where are you trying to delete the partition from? Windows or Ubuntu? The easiest way to do this would be booting from a live cd, then run gparted to edit the partitions. (press ALT+F2, then type in "sudo gparted").

/edit/ Sorry, misread the post :S, hibliss is right. If it was installed with wubi there will be no partition created.

---

### Post by azigma on 2009-06-23
Well that cleared that up, unfortunately  after I uninstalled then went to reinstall, I got:

Windows- No Disk

"Exception Processing Message c000013 Parameters 75b6bf7c 4 75b6bf7c 75b6bf7c"
can you help with that or should I be opening another thread?
And when I try to close the message, it just keeps reappearing.
Thanks for the replies

---

### Post by RJ12 on 2009-06-23
If you have any card readers unplug them first or even any external hard drives that you may have I think thats how it is fixed



P.S. I would stay away from Wubi becuase if you ever have to force reboot then you will corrupt your install and possibly even the Windows Install if you can I recommend partitioning it and dual booting but now I dont even use Windows no more

---

