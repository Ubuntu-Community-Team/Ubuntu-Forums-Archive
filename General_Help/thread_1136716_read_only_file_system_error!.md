---
title: "read only file system error!"
date: 2009-04-25
forum: General Help
---

### Post by linux_ocean on 2009-04-25
Hi. I want to copy some files to my flash disk, but i recive the error bellow:
[COLOR="Red"]" error while copying. the distination is read only."[/COLOR]

so i saw the permission of my flash disk where is loaded. and i put the result here for more information: 

> hossein@polaris-desktop:~$ cd /media
hossein@polaris-desktop:/media$ ls -l
total 16
lrwxrwxrwx 1 root    root    6 2009-04-24 11:13 cdrom -> cdrom0
drwxr-xr-x 2 root    root 4096 2009-04-24 11:13 cdrom0
drwx------ 5 hossein root 8192 1970-01-01 03:30 disk
lrwxrwxrwx 1 root    root    7 2009-04-24 11:13 floppy -> floppy0
drwxr-xr-x 2 root    root 4096 2009-04-24 11:13 floppy0
hossein@polaris-desktop:/media$ 



as you see the permission of disk for owner is full. but i am still unable to copy into it. I can't change the permission with "chmod" too!
what is your idea about this problem?

---

### Post by Monotoko on 2009-04-25
try copying them using sudo, if your trying to copy to the disk directory it doesnt look like it has permissions

---

### Post by linux_ocean on 2009-04-25
I did that, but i am still unable to copy any thing to my flash disk.

---

### Post by linux_ocean on 2009-04-26
I can solve it by formating the flash disk.

---

### Post by Robbyx on 2009-05-05
What did you do to reformat the SD? I have failed with the partition editor.

---

### Post by linux_ocean on 2009-05-08
> **Robbyx said:**
> What did you do to reformat the SD? I have failed with the partition editor.
I think you should unmount it first.
try: 
```
umount /dev/sdb1
```
with root permission.
then:
```
mkfs.vfat -F 32 /dev/sdb1
```
have a good time.

---

### Post by Robbyx on 2009-05-08
What I did was to buy a cheap card reader from ebay. Via my computer I reformated the disk and that took away the read only problem.

Robin

---

