---
title: "i have installed ntfs-3g but i can write to ntfs properly"
date: 2006-07-31
forum: Desktop Environments
---

### Post by jmrscoder on 2006-07-31
I have instaled fuse library and ntfs-3g in Ubuntu 6.06 modified the /etc/fstab, and tried to copy files to this  160gb ntfs partition, but after reboot the data has disappeared!

the moral of this history is: the ntfs-3g drivers are still beta!

i have reformated this partition to ext2 to more easy data recovery and a small partition of fat32 to transfer data to windows

have anyone else tried ntfs-3g?

---

### Post by msandersen on 2006-08-01
I installed it yesterday with no problems, and I've made some test writes of text files with no problems. 
I set up 2 new data partitions of equal size, one in NTFS, the other EXT3. I installed NTFS-3G on Linux, and the [EXT2IFS]("http://www.fs-driver.org/") filesystem driver on Windows to give it native support for Ext2/3. I'm going to test downloading more substantial files to each from the non-native OS. I've had Ext2IFS installed a little while with no problems actually. 
I just hate the idea of having to use the antequated FAT system for sharing. It doesn't handle partitions over a gig or two very efficiently, and has poor data-recovery. 
Naturally, since the specs for EXT2/3 are open, it's easier to make a safe driver for it as compared to reverse-engineering NTFS. NTFS-3G hasn't been out very long, and a few fairly minor known bugs exist while the developer is away for the month before they can be fixed. They are not critical though, except if your drive is full. It doesn't do error handling well at the moment, ie if you're writing a file and the drive doesn't have room for it all, it will fail, possibly without telling you.

---

