---
title: "Add 2nd hard drive and make it usable by all users"
date: 2009-02-22
forum: General Help
---

### Post by UranUtan on 2009-02-22
Hi,

I have started a thread asking how to add a 2nd hard drive [http://ubuntuforums.org/showthread.php?t=1073859](http://ubuntuforums.org/showthread.php?t=1073859)
I prefer to start another one to simplify things because the previous one is loaded with too much details.

Here is what I need: Adding a 2nd hard drive (IDE, 40 GB). It will be internal (assembled inside the computer), permanent and must be usable by all users. This means when UserX logs in, he/she can read, write, create folders, delete file/folder, etc. on this 2nd HD. By UserX I mean ALL user account on this machine.

Here is what I have done:
1- Adding 2nd HD, after log in, I see (by sudo fidsk -l) that it is recognized as /dev/sdb1

2- Ran GParted, deleted the previous NTFS partition. Created a Primary partition (on the entire disk), ext3. I also gave it a Label name.

3- Edited /etc/fstab and added the following lines:
> # /dev/sdb1
UUID=e172b709-228f-425d-980c-42d070623ede /media/idedrive2 ext3 defaults,users    0       2 

- The value for UUID was given by blkid 
- I have created /media/idedrive2 by sudo mkdir and made myself the owner (sudo chown -R MyUsername: /media/idedrive2

4-Reboot
- The drive is visible on the desktop under the name "41.2 GB Media"
- Only myself can write on this HD, all other users got permission denied.
- There is a folder named lost+found which contains nothing. I have tried to copy some dummy files and delete them, but the deleted file are not moved to lost+found.

Questions:

[COLOR="Red"]**Q1.**[/COLOR] How to change the disk label?

[COLOR="Red"]**Q2.**[/COLOR] How to make the drive Read/Write by ALL users

[COLOR="Red"]**Q3.**[/COLOR] Can I delete the lost+found folder?

Thank you very much in advance for any help.

---

### Post by taurus on 2009-02-22
What are the permissions of the mount point for /dev/sdb1--/media/idedrive2?

```
ls -la /media
```
You could do something like

```
sudo chmod -R 777 /media/idedrive2
```
and see if others can write to /media/idedrive2 now.

---

### Post by CowzRule on 2009-02-22
> **UranUtan said:**
> 
Questions:

[COLOR="Red"]**Q1.**[/COLOR] How to change the disk label?

Have a look at [this page]("https://help.ubuntu.com/community/RenameUSBDrive").

---

### Post by UranUtan on 2009-02-22
> **taurus said:**
> What are the permissions of the mount point for /dev/sdb1--/media/idedrive2?

ls -la /media
shows
drwxr-xr-x  4 myUsername  myUsername  4096 2009-02-22 00:38 idedrive2

After **sudo chmod -R 777 /media/idedrive2** then indeed other users can do read / write. BTW, If I tried 766 instead of 777, other users still has permission denied when trying to copy a file to this drive. It has to be 777. Strange, I though that the x flag was for execute. Actually it is for write. Rather confusing.

I think most of the case, we'll do chmod on the mount point. It would be simpler if there is an option in the fstab entry to say "give full permission to all users" or something to allow the chmod flag.

> **CowzRule said:**
> Have a look at [this page]("https://help.ubuntu.com/community/RenameUSBDrive").

**sudo e2label /dev/sdb1 NewLabelname**

works OK but must reboot to see the new name. I saw a few posts where someone suggested e2label. I tried but it didn't work. I didn't know that I have to reboot to see new name. I am used to Windows convention where the new Drive name takes effects immediately.

---

