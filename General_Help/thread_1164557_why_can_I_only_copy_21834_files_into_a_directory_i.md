---
title: "why can I only copy 21834 files into a directory in an external drive?"
date: 2009-05-19
forum: General Help
---

### Post by pcardoso on 2009-05-19
Hi,
I have a folder with a lot of (small) files that i want to copy into a folder in a external disk. However after 21384 (!?) files i get an error. Somethong like "disk full" (tried it in console, Konqueror, beyond compare). I'm sure to have a lot of free space (more than 150Gb).

Does any one know why? why 21834? 

the external drive is FAT32 and with "df -i" 
i get

Sistema de Ficheiros            Inodes IUsed IFree IUse% Montado em
/dev/sdb1                  0       0       0    -  /media/PCARDOSO250G


thkx,
PC.

---

### Post by Joeb454 on 2009-05-19
Are you copying any insanely large files? (i.e. virtual machine disks)

If so, because these are likely over 4GB, it wouldn't be able to write it to the disk, because FAT32 has a file size limit of 4GB :)

---

### Post by pcardoso on 2009-05-19
> **Joeb454 said:**
> Are you copying any insanely large files? (i.e. virtual machine disks)

If so, because these are likely over 4GB, it wouldn't be able to write it to the disk, because FAT32 has a file size limit of 4GB :)

No, it is just the opposite: they are small text files.

thkx,
PC.

---

### Post by mbeach on 2009-05-19
take a look at the link provided in the following
[http://help.lockergnome.com/windows2/file-folder-limits--ftopict450749.html](http://help.lockergnome.com/windows2/file-folder-limits--ftopict450749.html)

> 
A FAT32 directory can have 65,536 directory entries. Each file and
subdirectory takes from two to thirteen entries, depending on the
length of its name, so those entries can disappear long before you
think you've used them all up. Your total of 22,657 files could very
easily use 65,000 entries.

>2. Can this limit be changed?

No.

-- 
Tim Slattery
MS MVP(DTS)


---

### Post by pcardoso on 2009-05-20
> **mbeach said:**
> take a look at the link provided in the following
[http://help.lockergnome.com/windows2/file-folder-limits--ftopict450749.html](http://help.lockergnome.com/windows2/file-folder-limits--ftopict450749.html)

Thank you very much. Actually I have file names with something like 16 characters, which possibly explains my problem. 

**So, since some times I have to work on windows at school, my solutions is to convert it to NTFS? ** 

If so, I was looking around but I got a bit confuse (possibly because I looked at somehow old forums). I can make the convertion in several ways (make a copy and then format the drive using, for example, GParted or simply using an utility that I believe to come with windows) and access it using NTFS-3g.  

**But, what are the pitfalls of this convertion/using NTFS? Windows, without further software "bridges", doesn't recognize other file systems than FAT_ and NTFS, wright?**

Thank you again!
PC.

---

### Post by meganox on 2009-05-20
Yes, if you need your drive to work with Windows without having to install extra software NTFS is the only way to go.  There are ways to have Windows read Linux ext2/ext3 partitions but you would need administrator rights on every Windows box you wanted to use the drive with.

I don't know anything about 'converting' a drive with data on it to NTFS.  I would format it from scratch.

---

### Post by pcardoso on 2009-05-20
> **meganox said:**
> Yes, if you need your drive to work with Windows without having to install extra software NTFS is the only way to go.  There are ways to have Windows read Linux ext2/ext3 partitions but you would need administrator rights on every Windows box you wanted to use the drive with.

I don't know anything about 'converting' a drive with data on it to NTFS.  I would format it from scratch.

That's what I'll do.

Thank you ALL. 

PC.):P

---

### Post by rizman on 2009-05-20
If you have access to a windows machine, you can convert FAT32 drives to NTFS wothout data loss. I'm not positive that it works with external HDD, but I'm 100% sure that it works with "internal" HDD's. Though I see no reason why it won't work with external disks

See [http://support.microsoft.com/kb/307881](http://support.microsoft.com/kb/307881)

Open a command propmt and enter:
```

convert *driveletter:* /fs:ntfs

```

---

