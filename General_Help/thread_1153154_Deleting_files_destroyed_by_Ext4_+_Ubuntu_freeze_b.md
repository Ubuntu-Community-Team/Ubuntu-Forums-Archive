---
title: "Deleting files destroyed by Ext4 + Ubuntu freeze bug"
date: 2009-05-08
forum: General Help
---

### Post by utkjamie on 2009-05-08
The bug a lot of people have been experiencing lately with Ubuntu freezing up has struck me yet again and, unfortunately, I'm using Ext4 which means I've lost data.

Now I have a folder full of files that I cannot access nor delete. When I attempt to remove using *rm* I get:

> rm: cannot remove `name_of_file.ext': No such file or directoryWhen I run an *ls -l*, I get the following for each of the files:

> -????????? ? ? ? ?                ? name_of_file.extHow do I fix this? Even more, how do I get Ubuntu to stop destroying my data under Ext4??


Another problem I've noticed is that data destroyed under the Ext4 filesystem sometimes takes up space on the hard drive even though the file appears to have been completely destroyed (as opposed to the above problem). How do I recover this *phantom* disk space?

---

### Post by The Cog on 2009-05-08
My advice is to back up while you can, then reformat to ext3 and restore. Keep a watch for reports on the status of the bug. bear in mind that it may be Ubuntu specific, so reports of ext4 being reliable on other distros aren't a good indication in this instance.

---

### Post by utkjamie on 2009-05-09
> **The Cog said:**
> My advice is to back up while you can, then reformat to ext3 and restore. Keep a watch for reports on the status of the bug. bear in mind that it may be Ubuntu specific, so reports of ext4 being reliable on other distros aren't a good indication in this instance.

I'm not sure a "scorched earth" policy of wiping over 2 years of tweaks, customizations, and installs is the best solution. That's the kind of thing that made me drop Windows in the first place.

---

### Post by whoop on 2009-05-10
You probably already did this (but you never know), boot from a (jaunty) live-cd and run gparted, right-click on the partition with problems and click 'Check' to do a file system check.

I also assume that you used sudo in conjunction with rm...

---

### Post by utkjamie on 2009-05-10
> **whoop said:**
> You probably already did this (but you never know), boot from a (jaunty) live-cd and run gparted, right-click on the partition with problems and click 'Check' to do a file system check.

Actually, no. I haven't tried this. This is the first time I've seen this kind of problem. Not sure if it'll work because I think the Live CD is using the 2.6.27-11 kernel and the files are on an Ext4 partition, but I'll give it a shot when I get the chance. Thanks for the tip!

> **whoop said:**
> I also assume that you used sudo in conjunction with rm...
Yeah. This didn't work. I get "Stale NFS file handle" errors.

---

### Post by whoop on 2009-05-10
> **utkjamie said:**
> Actually, no. I haven't tried this. This is the first time I've seen this kind of problem. Not sure if it'll work because I think the Live CD is using the 2.6.27-11 kernel and the files are on an Ext4 partition, but I'll give it a shot when I get the chance. Thanks for the tip!


Yeah. This didn't work. I get "Stale NFS file handle" errors.

You most likely wont be able to read ext4 with gparted running on a 2.6.27 kernel. But the jaunty live-cd will work.
I think there is a chance that running the check with gparted and then a "sudo rm -f" on those files (to remove them) could work.

---

### Post by utkjamie on 2009-05-15
Sorry for the delay in updating. Running fsck cleared up the problem. I had been assuming fsck runs automatically at reboot and would have cleared these "files" out but apparently that wasn't the case. All appears fine now. Thanks!

---

