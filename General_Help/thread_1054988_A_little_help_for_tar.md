---
title: "A little help for tar?"
date: 2009-01-30
forum: General Help
---

### Post by aryzing on 2009-01-30
Ok, so im trying to use tar as my backup utility. Now, apparently its working, but not as i expect it to.

Scenario: A folder called stufftobackup/ has 3 documents doc1 doc2 and doc3, and ```
tar -cvf backup.tar stufftobackup/
``` has been executed once.

If i modify a file (say doc1) and execute ```
tar -uvf backup.tar stufftobackup/
``` it appends the new modified doc1 to the end of the tar file correctly. However, the original, unmodified doc1 becomes inaccesible. Executing the comand ```
tar -tvf backup.tar
``` will produce ```
stufftobackup/
stufftobackup/doc1
stufftobackup/doc2
stufftobackup/doc3
stufftobackup/
stufftobackup/doc1
```

Further information: When i open backup.tar with GNOME's file archiver File Roller 2.24.1 i can see both the new and old doc1, yet no matter which one i doble-click, it always opens the new one. Running the command ```
tar -xvvf backup.tar
``` will also only extract the new one.

If possible, i would like to be able to acces older versions of files or simply replace a file in backup.tar with the newer version. 

Thanks all in advance!

---

### Post by sedawk on 2009-01-30
Try
```

tar xvf --occurence=1 stufftobackup/doc1

```

---

### Post by unutbu on 2009-01-30
[list]
[*]To replace an older stufftobackup/doc1 file with a newer files version in backup.tar, you could do this:
```

tar -f backup.tar --delete stufftobackup/doc1
tar -f backup.tar --update stufftobackup/doc1
```
[*]Don't do this:
```
tar -cvf backup.tar stufftobackup/
ls -l backup.tar
```
modify stufftobackup/doc1
```
tar -uvf backup.tar stufftobackup/ # This doubles the size of backup.tar
ls -l backup.tar

```
The "ls" commands will show that backup.tar doubles in size, because you've now got two copies of everything in backup.tar. 
[B]
I have not found a way to extract both copies of a file from a tar archive.[/B]
[*]Are you backing up stufftobackup/ onto an ext2/ext3 filesystem? If so, rsync may be a better solution. The advantages are:
[list]
[*]rsync copies the directory structure as is, instead of archiving it. This allows you to navigate through the backup directories and pull out individual files easily. With tar, extracting individual files is incredibly slow when the tar file is big.
[*]rsync can do fast incremental updates of large directories. From the man page:
> 
It is famous for its delta-transfer algorithm, which reduces the amount
of data sent over the network by sending only the differences between the source
files and the existing files in the destination.  Rsync is widely used for back&#8208;
ups and mirroring and as an improved copy command for everyday use.
Thus you can use 
```

sudo rsync -a --delete stufftobackup/ backup/
```
with impunity even if stufftobackup is huge, and rsync will only copy the little bits and pieces of modfied files, or newly created files. The --delete flag tells rsync to delete files in backup/ that are not present in stufftobackup/.
[/list]
The only time I think tar is better (or necessary) is if you are backing up onto a non-ext3 filesystem such as a CD (iso9660) or onto a Windows partition (FAT32 or NTFS). In these cases, tar will save the ownership, permissions and links, while rsync can not since these features are not present on iso9660, FAT32 or NTFS filesystems.
[/list]


**@sedawk**: Which version of tar are you using? Ubuntu's tar does not have an --occurence flag. (I also tried --occurrence). The man page does not mention such an option either.

---

### Post by aryzing on 2009-01-30
thanks a bunch. ive done a few test runs with rsync and it works perfectly. From now on i am using this to backup my files. Once again, thanks for the help!

---

