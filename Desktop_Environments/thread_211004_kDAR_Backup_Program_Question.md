---
title: "kDAR Backup Program Question"
date: 2006-07-07
forum: Desktop Environments
---

### Post by JackRazz on 2006-07-07
Hi everyone,
I'm a Linux newbie using kdar on a slax based usb stick to back up my newly installed ubuntu linux on my hard drive.  Fantastic little utility.  I tried out the differental backup the other day and ran into problems.  I get a bunch of hard link errors.  Specifically, I'm backing up files on ext3 partitions to DAR backup files on a FAT32 partition.  I don't get any errors if it isn't a differential backup.

This is a description of the kdar module I'm using for the versions.    
[INDENT]DAR version 2.3.1 released 6/26/06 (libdar.4) command line backup utility
 the older KDAR 2.07 (libdar.3) from the kdar squashfs 2.2 module
 created by Slax Member Quax converted to a squashfs 3.0 module.[/INDENT]

I'm assuming that hard link errors are bad.  Is there a simple way to avoid the errors?

Thanks - Jack

---

### Post by aysiu on 2006-07-07
FAT32 partitions have a hard time with differential backups--that's what I've found in using rsync. I think it may have something to do with the way it stores upper- and lower-case letters.

---

### Post by JackRazz on 2006-07-08
aysiu,
Thats what I suspected, do you know if fat has the same issues as fat32?  I've even had problems copying links from my fat32 usb stick when they originated from windows.  Anyone else have any personal experience with this?

I'll just avoid differentials (and they were so cool).  Might try backing up to a file on the ext3 and then copying to the fat and see if that works.

Thanks aysiu - JackRazz

---

### Post by aysiu on 2006-07-08
FAT16, you mean? I think all the FATs operate pretty much the same way.

When you say you've had problems copying links, could you elaborate a bit? Not accessible? Some kind of error? Upper-/lower-case issues?

---

### Post by JackRazz on 2006-07-09
I just checked and no, it's FAT32.  I asked in the ubuntu irc channel and remember a comment FAT32 was fine.  Should I change it to FAT16?

I'll get back on the details on the shortcuts.

Thanks - JackRazz

---

### Post by aysiu on 2006-07-09
I don't believe FAT16 or FAT32 will work for differential backups.

---

### Post by JackRazz on 2006-07-10
aysiu,
Thanks for the info.  I'll just use full backups and move on.  Linux backups are pretty small at the moment anyway and disk space is dirt cheap.

Thanks for all the help - JackRazz

---

