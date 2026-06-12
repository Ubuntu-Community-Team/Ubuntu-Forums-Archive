---
title: "Ecryptfs on external drive shared with Windows"
date: 2009-02-13
forum: General Help
---

### Post by sepelester on 2009-02-13
I'm planning to buy an external usb drive to use with both Windows and Linux computers. I'm planning to use ntfs as file system as ntfs-3g handles it well and ext3-ifs is not an alternative under windows.

Is it possible to encrypt a folder on an ntfs partition with ecryptfs? I only need the contents under Linux, so ecryptfs suits me very well. 

I will obviously not be able to read the contents of the folder in windows, but will I run into problems mounting the drive? Or will windows try to "fix" the folder, effectively destroying my precious encrypted data?

---

### Post by anandkumargupta on 2009-08-22
> **sepelester said:**
> I'm planning to buy an external usb drive to use with both Windows and Linux computers. I'm planning to use ntfs as file system as ntfs-3g handles it well and ext3-ifs is not an alternative under windows.

Is it possible to encrypt a folder on an ntfs partition with ecryptfs? I only need the contents under Linux, so ecryptfs suits me very well. 

I will obviously not be able to read the contents of the folder in windows, but will I run into problems mounting the drive? Or will windows try to "fix" the folder, effectively destroying my precious encrypted data?

I tried the same thing with Seagate external usb drive where that was formated with HPFS/NTFS. Interesting part is I am able to mount and encrypt. But when I try to decrypt it it shows strange error. First the file don't use to decrpt and second when I try to unmount it shows directory permission ans size like 

root@anand-laptop:/media/FreeAgent Drive/Seagate Sync# ls -l
ls: cannot access test: Device or resource busy
total 8
drwxrwxrwx 1 root root 4096 2009-08-17 01:45 Backup
drwxrwxrwx 1 root root 4096 2009-08-17 00:23 Panther
d????????? ? ?    ?       ?                ? test
root@anand-laptop:/media/FreeAgent Drive/Seagate Sync# 

Where test directory I try to unmount with command "umount test".
I think using ecryptfs using on NTFS partition is a bad idea. :)

---

### Post by anandkumargupta on 2009-08-22
> **sepelester said:**
> I'm planning to buy an external usb drive to use with both Windows and Linux computers. I'm planning to use ntfs as file system as ntfs-3g handles it well and ext3-ifs is not an alternative under windows.

Is it possible to encrypt a folder on an ntfs partition with ecryptfs? I only need the contents under Linux, so ecryptfs suits me very well. 

I will obviously not be able to read the contents of the folder in windows, but will I run into problems mounting the drive? Or will windows try to "fix" the folder, effectively destroying my precious encrypted data?

I tried the same thing with Seagate external usb drive where that was formated with HPFS/NTFS. Interesting part is I am able to mount and encrypt. But when I try to decrypt it it shows strange error. First the file don't use to decrpt and second when I try to unmount it shows directory permission ans size like 

root@anand-laptop:/media/FreeAgent Drive/Seagate Sync# ls -l
ls: cannot access test: Device or resource busy
total 8
drwxrwxrwx 1 root root 4096 2009-08-17 01:45 Backup
drwxrwxrwx 1 root root 4096 2009-08-17 00:23 Panther
d????????? ? ?    ?       ?                ? test
root@anand-laptop:/media/FreeAgent Drive/Seagate Sync# 

Where test directory I try to unmount with command "umount test".
I think using ecryptfs using on NTFS partition is a bad idea. :)

---

### Post by anandkumargupta on 2009-08-22
I tested ecryptfs with FAT16 and that was working very much fine. I tested with my 2GB M2 card of my mobile.

---

### Post by alexgenaud on 2010-11-11
I synchronize/backup hundreds of GB from an encrypted ext4 partition to an NTFS drive (encrypted and not). The only annoyance I have is file NAME sizes. Very long plantext file names (70+ chars) are encrypted with an even longer file name, which I can not transfer to NTFS (to be fair, I'm using unison which creates temp files with slightly longer names and it is these temp files that cause error).

I find that filenames under 65 characters sync perfectly between NTFS and EXT4, both encrypted and unencrypted.

---

