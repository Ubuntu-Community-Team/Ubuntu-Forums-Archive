---
title: "Backup"
date: 2008-07-24
forum: Desktop Environments
---

### Post by jerrywo on 2008-07-24
I've got a clean install of Ubuntu on a linux-only machine.  I'd like to clone my hard drive, essentially making it bootable if necessary.  My partitions are:
/boot
/
swap
/home

I was just going to repartition my external HD which is identical to the one in my machine...and copy stuff over to it.  It can't really be that simple can it?

I was running Fedora 7 (and then 8).  I simply used a little RSYNC script that I wrote.  I assume, once I get my info copied onto the external drive, I can use a similar script. 

I do not leave my machine on 24/7, so I don't care about automated backups.
Jerry W.

---

### Post by Tim Sharitt on 2008-07-24
```
"dd if=/dev/sda of=/dev/sdb
```
Should work, but may take a while. Use the names of the drives on your machine of course.

---

### Post by jerrywo on 2008-07-27
A long time indeed!

I did a dd command, as it turns out, my drives were the same as your example.  **One full day transpired with no end in sight.**  So I was able to find the process ID number, then I killed it.

I re-entered the DD command but appended "bs=1024k" to the end of the command string and my drive was cloned in 3 hours.  Apparently the default block size for dd is 512 Bytes.  This changed it to a MB.

Thanks for your help

Now I'm gonna see about re-writing my little RSYNC script or using "backup" which I downloaded a few days ago

I also want to see if I can boot from my external drive.

---

