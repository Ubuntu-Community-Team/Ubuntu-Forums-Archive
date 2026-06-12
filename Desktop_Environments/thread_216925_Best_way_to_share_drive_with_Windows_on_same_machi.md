---
title: "Best way to share drive with Windows on same machine?"
date: 2006-07-16
forum: Desktop Environments
---

### Post by detzx on 2006-07-16
OK, I have my music and movies on ntfs drives but now I want to add(write) and stuff from linux.  I know there is support for ntfs but I don't trust it.  I tried to convert to fat32 but I couldn't get it to work so I moved all the files to another drive and I tried to reformat with fat32 but it wont let me do the partitions greater than 200GB(that correct) so it's a paint to have 3-4 partitions split up. Is there another way I can share a drive between them and have the whole drive available?

---

### Post by Thund3rstruck on 2006-07-16
Ok, making sure I have this correct. You have several fat32 partitions that you want to make available to linux?

modifiy your /etc/fstab file to mount these partitions somewhere in /media or /mnt. Take a look at your fstab or search the forum for the exact syntax. It's actually really easy to do if I remember correctly.

---

### Post by detzx on 2006-07-16
> **Thund3rstruck said:**
> Ok, making sure I have this correct. You have several fat32 partitions that you want to make available to linux?

modifiy your /etc/fstab file to mount these partitions somewhere in /media or /mnt. Take a look at your fstab or search the forum for the exact syntax. It's actually really easy to do if I remember correctly.

Nope, currently they are still ntfs because I can't find a way to conver them and when I move the data and tried to reformat as fat32 it would only let me make the paritions on the drive 200GB(320GB drives) and that's a pain. Im looking for a way, if there is another, to share the data other than doing fat32 partition.

---

### Post by flaxx on 2006-07-16
I think you should try captive-ntfs (using the native windows libraries to write on ntfs partitions). My experience with captive are great, I didn't use / install it on Ubuntu though.

---

### Post by RRS on 2006-07-16
You may also want to check out
[Extfs.sys]("http://www.fs-driver.org/index.html") allowing you to read/write to Ext3 from windows.

By storing your files in Ext3 Linux won't have any problems and you get rid of the size restrictions. Fat32 only allows files to 4g  which could be a problem for some movies.

---

### Post by Lester King on 2006-07-16
I am dual-booting and I've got 1 hard drive as my Windows drive formatted to NTFS. 1 partition formatted ext3 for ubuntu a second partition on that drive formatted ext2. And a third drive formatted ext2. In windows I use ext2 read/write drivers to access those. It works pretty great. All movies and music are available on the ext2 formatted drives in both windows and linux. The newest version of Ext2 IFS for Windows ([http://www.fs-driver.org/](http://www.fs-driver.org/)) apparently will write to ext3, but when I started it didn't. I haven't had any trouble with these drivers in windows.

---

