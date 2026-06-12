---
title: "Backup files not recognised by me"
date: 2009-01-17
forum: General Help
---

### Post by Robbyx on 2009-01-17
In December I had been using a backup program. As a result of the change to 8.10 I did not reistall the backup prog. I would like to restore some of the files in it but do not know which prog I used. I think it was simple backup and restore. I have just installed it but it does not show up in the applications.

How do I put it into the applications?

Does anyone recognise this file structure?
Directory name:
2008-12-13_07.36.49.534840.robin.ful

Files in dir:

excludes
files.tgz
flist
fprops
packages
partitions
ver 
   content of version is one line = 1.4

Robin

---

### Post by Zill on 2009-01-17
It looks like you used Simple Backup (sbackup for short!).

This should be in menu System, Administration, Simple Backup Config or Simple Backup Restore.

---

### Post by Robbyx on 2009-01-17
When I point simple restore at the archives it does not recognise any of them. Any ideas?

What I have tried is opening one of the folders and trying to open the files.tgz inside it. It takes a very long time to open. So long that I wonder if it will ever open.

R

---

### Post by Robbyx on 2009-01-18
Using the archive manager in sudo mode the following error occurs when trying to open the files:

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now 

simple backup's restore is also  not opening the backup files. 

Do you know what  I can do about it?

R

---

### Post by Zill on 2009-01-18
> **Robbyx said:**
> When I point simple restore at the archives it does not recognise any of them. Any ideas?

What I have tried is opening one of the folders and trying to open the files.tgz inside it. It takes a very long time to open. So long that I wonder if it will ever open.

What do you mean by "does not recognise any of them"?  The sbackup window *should* show the path to the backup archive.  If this is not correct then change it to the correct path.

The box *should* have a pulldown list called "Available backups"  Click on the arrow to show your required archive, then select it.

A list of folders/files should then appear below so you can select which ones to restore.

If you can select any of these files then it does take quite a while to restore them. :-(  Just be patient!

---

### Post by Robbyx on 2009-01-18
Thank you for your response. Eventually I hit on the idea of changing the default location within the setup and then the available backups were recognised. Previously I had changed the location within the restore section only and that seemed not to work.

---

### Post by Zill on 2009-01-18
> **Robbyx said:**
> Using the archive manager in sudo mode the following error occurs when trying to open the files:

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now 

simple backup's restore is also  not opening the backup files. 

Do you know what  I can do about it?

I may be wrong on this but I *think* I recall seeing this myself in the past. :-(

I never really got to the bottom of it but think it may be related to file sizes and/or opening the files with the Archive Manager (File Roller).  Using SBackup, rather than File Roller, seemed to work OK for me.

However, I have been fortunate in that I have never needed to restore a *full* backup archive so have only tested it on a few example directories/files.

I suggest you first try to restore just one or two small files from Sbackup to see if that works.

---

