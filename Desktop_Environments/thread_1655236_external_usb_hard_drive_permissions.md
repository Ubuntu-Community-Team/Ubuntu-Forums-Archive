---
title: "external usb hard drive permissions"
date: 2010-12-29
forum: Desktop Environments
---

### Post by unfinishedsweet on 2010-12-29
Hi There

I am digging the forum through and cannot find the answer. My problem is, the usb hard drive when plugged in get automatically mounted what is great. Unfortunately I get only read permissions, while need write too.

There are no any entries in fstab, so I do not know what does handle automounting and how to edit options to force mounting with write permission to user (root obviously can write). Are they hald options or any other app does this? Where to edit them? The drive is not permanently ON, just switch it when need, so it has to work every time I put it on.

I use xubuntu with Thunar.

Regards
Mr. P

---

### Post by Bucky Ball on 2010-12-29
What are the permissions now? For the user or root or won't let you see them?

---

### Post by unfinishedsweet on 2010-12-29
I can see all the files as a user, cannot write though. Root can do everything. On the ext partitions I can give permissions to folders and that's fine. Worse is with jfs even root cannot write I think. Cannot check it now as too many operations on that disk at the moment. There also is few ntfs partitions on that disk I would like to have accessible to write by user straight after auto mounting.

---

### Post by Bucky Ball on 2010-12-29
You need be a bit more specific.

The external drive you are trying to write to is jfs? NTFS?

When you right click on the drive, hit PROPERTIES, then PERMISSIONS, what do you see?

---

### Post by unfinishedsweet on 2010-12-29
It's multi partition disk. On ext partition the root is owner and has write permissions, on jfs partition user is the owner but nobody has write access as it is read-only file system. Is jfs fully read write supported in generic kernel by the way?

---

### Post by Bucky Ball on 2010-12-29
This might be of some help.

[http://www.linux.com/archive/feed/119025](http://www.linux.com/archive/feed/119025)

Right click on that partition and change the permissions if you can.

---

### Post by unfinishedsweet on 2010-12-29
the link doesn't solve my problem. I used to use jfs with my previous machine controlled by gentoo linux where disk came from. Just don't know why it is automatically mounted as a read-only file system ?

---

### Post by Bucky Ball on 2010-12-29
'Tis odd.

---

### Post by unfinishedsweet on 2010-12-29
```
chmod: changing permissions of `/media/disk-5/': Read-only file system
```

---

