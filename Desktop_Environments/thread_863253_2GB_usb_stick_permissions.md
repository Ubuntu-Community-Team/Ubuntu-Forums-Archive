---
title: "2GB usb stick permissions"
date: 2008-07-18
forum: Desktop Environments
---

### Post by peterthewolf on 2008-07-18
In the usb sticks properties permission tab there is this comment

"The permissions of "disk" could not be determined."

Anyone have a suggestion to fix.

In practice I can copy .txt files to the stick but if I try to copy .mpg file I get "permission denied".

---

### Post by Potatoj316 on 2008-07-18
Thats strange, you can write, but only one file type.  Is the disk full?

---

### Post by peterthewolf on 2008-07-18
No 
The basic properties tab says
   Name:    2.1 GB Media
   Type:    folder
   Contents: 1 item, with size 16.0 KB
             (some contents unreadable)
   Location: on the desktop
   Volume:  2.1 GB Media
   Free space: 1.8GB
   Modified: Fri 10 Jul 2008 12:50:30 BST

   yellow 133.0 MB used
   blue   1.8 GB free
   Total capacity: 1.9 GB
   Filesystem type: ext3

This is after setting up anew via partition manager.

---

### Post by Potatoj316 on 2008-07-18
Ok try this (im not too familiar with this command so it may be a little off but wont do any damage to your computer or HD)
```
sudo chown [path to HD mount point] [your account name]
```

---

### Post by jimv on 2008-07-18
Just format it as FAT and permissions won't be an issue.

And that permissions tab says the same thing with my thumbdrive, and it doesn't seem to affect anything.

There's no benefit to having EXT3 on the thumbdrive instead of FAT, in spite of what others may claim.  Besides, if for some unforeseen reason you need that thumbdrive for a Mac or PC, they'll see FAT, but not EXT3.

---

### Post by Potatoj316 on 2008-07-18
Fat is usually the default on flash drives.  (when formating you will have to call it fat32)

---

### Post by peterthewolf on 2008-07-18
Thank you Fat32 works fine. A bit of disappoint in linux though since I have no likelihood of using in mac or windows so ext3 should be good enough.

---

