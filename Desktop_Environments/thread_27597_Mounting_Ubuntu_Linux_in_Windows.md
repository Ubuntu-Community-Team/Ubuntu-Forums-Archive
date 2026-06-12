---
title: "Mounting Ubuntu Linux in Windows"
date: 2005-04-16
forum: Desktop Environments
---

### Post by Topper on 2005-04-16
I've followed the guidelines on how to get windows mounted in Ubuntu in the [Ubuntu Starter Guide](http://ubuntuguide.org/temp/#automountntfs).

Now, my question is how to do the opposite: How can I mount Ubuntu in Windows XP? Is it possible?

I got some programs in Windows that I want to use, but I'd prefer to do the majority of my work in Ubuntu...

---

### Post by nad on 2005-04-16
It seems that you just want a shared file system someplace. As writing to a ntfs filesystem is still experimental and therefore possibly buggy, set up a new partition with a fat32 (vfat) filesystem. Both operating systems will be happy with this. For example, if you were to set up mozilla mail on both operating systems, you could specify one location for your data and access it from each.

XP will automatically see a vfat file system. You may mount it wherever you wish in ubuntu.

Dan M

---

### Post by Topper on 2005-04-16
Ok, thanks. I saw on Ubuntu guide that Linux can't (well) write to NTFS, so with hindsight I should have formatted with FAT32. I would rather not reformat Windows, so maybe I'll just reinstall Ubuntu and i the process set up a partition as FAT32...

But anyway thank you for the help

---

### Post by derrick1985 on 2005-04-16
[QUOTE=Topper]Ok, thanks. I saw on Ubuntu guide that Linux can't (well) write to NTFS, so with hindsight I should have formatted with FAT32. I would rather not reformat Windows, so maybe I'll just reinstall Ubuntu and i the process set up a partition as FAT32...

But anyway thank you for the help[/QUOTE]
Linux doesn't like FAT32.

Try this: I don't know for sure if in the Ubuntu install, when it asks for formatting hard drives, that it can do fat32, but make a partition using whatever program you wish (qt_parted works great, and it's free, you might be able to get it through apt-get in the universe repositories, i'm not too sure.) You can download this cd [http://www.sysresccd.org/](http://www.sysresccd.org/) and make a fat32 parition that way, take it out of your windows (resize and format the free space) and then you have your WindowsXP NTFS (XP likes NTFS) Ubuntu Linux ext3/ext2 (again, linux likes linux partitions) and a fat32 (windows doesn't mind it, and linux can read and write to it!) and

> Both operating systems will be happy with this. For example, if you were to set up mozilla mail on both operating systems, you could specify one location for your data and access it from each.

No problem, right?

---

### Post by danj205 on 2005-04-17
You can try EXT2IFS. It is a driver for Windows NT/XP that lets Windows read Linux drives. Note, that just has how Linux cannot write to NTFS drives, Windows cannot write to Ext2/3 drives.

You can try it out at [http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm).

---

### Post by bored2k on 2005-04-17
[QUOTE=danj205]You can try EXT2IFS. It is a driver for Windows NT/XP that lets Windows read Linux drives. Note, that just has how Linux cannot write to NTFS drives, Windows cannot write to Ext2/3 drives.

You can try it out at [http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm).[/QUOTE]
 Not necessary. [http://ubuntuguide.org/4.10/index.html#readlinuxpartitionsinwindows](http://ubuntuguide.org/4.10/index.html#readlinuxpartitionsinwindows) worked for me [ext3 needed].

---

