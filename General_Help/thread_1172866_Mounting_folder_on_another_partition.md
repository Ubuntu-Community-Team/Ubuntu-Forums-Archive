---
title: "Mounting folder on another partition"
date: 2009-05-29
forum: General Help
---

### Post by CroEragon on 2009-05-29
Hello guys.

Is there a way of transparently linking certain folder in my home folder to folder on another partition. Basically, I want to expand available free storage in my home folder without actually moving the whole thing on separate partition. Once done, no application that interacts with it will be able to tell on which physical disk data is on. I have both my Windows and Jaunty installed on small separate partitions (20GB each). With Windows, when I need more space for games or something else, I just install/place it on NTFS storage partition. But most of the programs (or their user data) in Ubuntu insist on being placed in /home which is located on small 20GB partition. I know you can make /home to be separate partition, but I want to have all of data in one place, just accessed by OS used at the time. 
Besides, repartitioning isn't an option anyway, nor is re-installing of current Windows or Ubuntu installations or messing with bootloaders.

Maybe something can be done to act similarly to how NTFS drives are mounted now, but instead of mounting whole drive, I'd mount one folder on storage partition and instead of accessing it on /media/drive-1/ I'd access it from /home/folder-on-other-partition/

Any suggestions?

Thanks in advance.

---

