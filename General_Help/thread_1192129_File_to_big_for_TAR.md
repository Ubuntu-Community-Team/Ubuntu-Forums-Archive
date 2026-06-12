---
title: "File to big for TAR?"
date: 2009-06-19
forum: General Help
---

### Post by mharrison on 2009-06-19
I found the following documentation on using TAR to backup my system..
[URL="https://help.ubuntu.com/community/BackupYourSystem/TAR#Additional%20resources"]https://help.ubuntu.com/community/BackupYourSystem/TAR#Additional%20resources
[/URL]

I modified it to just back my home directory up to an internal hard drive I use to keep my downloaded files to.  When the backup gets to my VirtualBox directory it kicks back an error saying the file is too large when it is trying to back up the one VDI file I have in there.  

I know I can just copy the folder to the backup drive, but I wanted it all in a compressed file so I can simply extract it should I need to restore anything and not have to dig through tons of files.

Is there a way I can do this or is there a size limit to the files I can compress with TAR?

---

### Post by geirha on 2009-06-19
Tar has no size limit, but filesystems does. What filesystem are you putting the tar on?

---

### Post by mharrison on 2009-06-19
FAT32...I use the drive to backup my wife's Windows drive as well.

---

### Post by yeats on 2009-06-19
FAT32 has a 4GB file size limit...

---

### Post by mharrison on 2009-06-19
> **chrissharp123 said:**
> FAT32 has a 4GB file size limit...

You know...I was wondering that....It has been so long since I have worked in Windows with FAT32....Normally when I have to it is with NTFS...and for the past 4 months I have only used Windows at work, so I have been trying to purge my brain of all things Microshaft.

---

### Post by mharrison on 2009-06-19
I ended up solving it...I reformatted to EXT4, got the UUID and copied the line in FSTAB for / and modified it to point to /media/Backup after I created the folder.

So far so good.

Thanks for the help!

---

