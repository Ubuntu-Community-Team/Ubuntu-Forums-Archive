---
title: "Read-only hard disk"
date: 2011-12-18
forum: Desktop Environments
---

### Post by Erufailon on 2011-12-18
I stumbled upon a problem that has never occured to me and I need some help. I use 2 external hard disks where I store my multimedia files (mp3,mkv) and I use them both with Windows 7 and Ubuntu 11.10 (dual boot). Yesterday I noticed that I can't anymore create folders or change anything in the disks. That is in Ubuntu but in Windows all are fine. When I go to nautilus properties I noticed that the permission for Owner is "Access Files", I tried to change it to "Create and delete files" but a message appeared "Sorry, could not change the permissions of "Elements": Error setting permissions: Read-only file system". So I thought that if I sudo (gksu) nautilus all would be ok and I would be able to change the permission but to my disappointment the same message appeared and I don't know anything else. I would be very grateful for some help.
Thank You,

---

### Post by typhoon_tip on 2011-12-18
How the disk is formatted ? If you have MKV, I suppose is NTFS.

Check that you have installed ntfs-3g package:
```
sudo apt-get install ntfs-3g
```

---

### Post by Erufailon on 2011-12-18
Wow thanks, it worked right away. The strange thing is that I didn't installed any new programs the last few days except the normal updates from Update Manager so I don't know how that happened but I'm very happy for your help typhoon_tip, Thank you very much.

---

### Post by typhoon_tip on 2011-12-20
Glad it worked. It is possible that it was unintentionally removed... it's just a small library indeed, but very precious ! :P

---

