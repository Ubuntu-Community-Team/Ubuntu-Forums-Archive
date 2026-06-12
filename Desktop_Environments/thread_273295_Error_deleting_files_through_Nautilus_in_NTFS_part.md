---
title: "Error deleting files through Nautilus in NTFS partition"
date: 2006-10-07
forum: Desktop Environments
---

### Post by lawina on 2006-10-07
I installed ntfs 3g and my fstab has the following entry for my windows partition.

/dev/hda1    /media/windows    ntfs-fuse    auto,gid=1001,umask=0    0    0

I am able to goto the terminal and able to 
cd /media/windows and delete files out there using 'rm' command.
However I am not able to delete files with Nautilus. If I try to do so, it gives me error windows saying..

" Error "Generic error" while deleting "/media/win...1997_.mp3" 
Would you like to continue?  "

I am able to create new files and folders with nautilus in the same folder. I am also able to edit those files. But I cannot DELETE the same.

Has anybody encountered the same behaviour?

---

### Post by lawina on 2006-10-08
Is there a log file which I can track for Nautilus?

---

### Post by givré on 2006-10-14
lawina, if you say you use ntfs-3g, why do you mount your HD with ntfs-fuse?
With the old ntfs-fuse device, you are likely to get this kind of error, but not with ntfs-3g.

Follow this guide : [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

