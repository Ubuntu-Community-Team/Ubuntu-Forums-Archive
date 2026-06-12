---
title: "Trouble Booting Up Ubuntu"
date: 2009-03-18
forum: General Help
---

### Post by h2o4444 on 2009-03-18
I've been using Ubuntu for almost 3 months and just recently it stopped booting. I even tried to load it in safe mode. I don't even see the login screen. I get a message that says:

> An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system started. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.

The root filesystem is currently mounted in read-only mode. A maintenance shell will now be started.

After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: no job control in this shell
root@ubuntu:"#

If no one can help me fix this problem then I might reinstall everything, which will be a pain. Or I might just wait for 9.04.

As a side note, I used Wubi to install Ubuntu.

---

### Post by linuxisevolution on 2009-03-18
> **h2o4444 said:**
> 

As a side note, I used Wubi to install Ubuntu.

<snip>

---

### Post by h2o4444 on 2009-03-18
You are correct, the file system is NTFS. However my computer does not have a CDROM drive. I installed Ubuntu by loading the ISO into daemon tools and installed it from there. If it's a filesystem problem then why did Ubuntu work for 3 months when it should just have crashed due to the filesystem?

---

### Post by linuxisevolution on 2009-03-18
> **h2o4444 said:**
> You are correct, the file system is NTFS. However my computer does not have a CDROM drive. I installed Ubuntu by loading the ISO into daemon tools and installed it from there. If it's a filesystem problem then why did Ubuntu work for 3 months when it should just have crashed due to the filesystem?

It could be if you did not restart correctly. NTFS can really be a pain in the behind when it comes to *improper* reboots...

---

### Post by linuxisevolution on 2009-03-18
I would suggest you buy a cdrom drive and do it the correct way:popcorn:

This one is only $13:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827106086](http://www.newegg.com/Product/Product.aspx?Item=N82E16827106086)

This one has a bit better ratings for $18:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827118024](http://www.newegg.com/Product/Product.aspx?Item=N82E16827118024)

This currency is in USD btw(united states).

Also, you could borrow a cdrom drive.

---

### Post by meierfra. on 2009-03-18
At the "root@ubuntu" prompt type "fdisk -lu" to determine the device name of the "ubuntu  partition" (it probably is /dev/sda1). Then type

fsck -y /dev/sda1

(replace "/dev/sda1" be the correct device name)

Once the file system check is done, use "Ctrl+D"  (press the Ctrl key and D  at the same time) to continue booting.

---

### Post by h2o4444 on 2009-03-18
I wish someone can solve this NTFS issue since most computers are Windows and Windows use NTFS. I guess I'll wait for 9.04 to come out then test out Ubuntu.

---

### Post by linuxisevolution on 2009-03-18
> **meierfra. said:**
> At the "root@ubuntu" prompt type "fdisk -lu" to determine the device name of the "ubuntu  partition" (it probably is /dev/sda1). Then type

fsck -y /dev/sda1

(replace "/dev/sda1" be the correct device name)

Once the file system check is done, use "Ctrl+D"  (press the Ctrl key and D  at the same time) to continue booting.

He is not using a Linux filesystem, so fsck will not work.

(it will say ntfs driver not found or something similar)

---

### Post by linuxisevolution on 2009-03-18
> **h2o4444 said:**
> I wish someone can solve this NTFS issue since most computers are Windows and Windows use NTFS. I guess I'll wait for 9.04 to come out then test out Ubuntu.

It's not an Ubuntu issue. If Windows isn't restarted properly the same thing can happen. Give or take.

Linux works fine for writing/reading NTFS.

You can just reinstall Ubuntu with wubi.

---

### Post by meierfra. on 2009-03-18
> He is not using a Linux filesystem, so fsck will not work
The OP is clearly logged into  a linux file system. (It is  a linux file system  located inside a file on an ntfs partition)

---

### Post by linuxisevolution on 2009-03-18
> **meierfra. said:**
> The OP is clearly logged into  a linux file system. (It is linux file system  located inside a file on an ntfs partition)

I thought it was a partition on an NTFS  filesystem? So you mean like a ubuntu.ext3 file? I use those for development :)

@OP, go ahead and try fsck, you got nothing to lose ;)

---

### Post by meierfra. on 2009-03-18
> So you mean like a ubuntu.ext3 file? 

Yes.  Wubi uses  a large file on    an ntfs partition  to create a virtual disk. And on that disk its creates an ext3 file system, which behaves just like a regular ext3 file system

---

### Post by linuxisevolution on 2009-03-18
> **meierfra. said:**
> Yes.  Wubi uses  a large file on  the  an ntfs partition  to create a virtual disk. And that disk its creates an ext3 file system, which behaves just like a regular ext3 file system

I know what it is, I just didn't know thats what it did... neat.... But if window's partition DOES get corrupted, bye bye file...

---

### Post by h2o4444 on 2009-03-19
I tried fdisk -lu and I get some info about my HDD like /dev/sda 60.0 GB... Then I did fsck -y /dev/sda and I get error while loading shared libraries...

So I guess I'm stuck at 0 again. I just don't understand why Ubuntu has worked for me for nearly 3 months (even it had some annoyances and other buggy things) but now it doesn't even boot up. I really like Ubuntu and if it weren't for these annoyances then i would have made the full switch. Although there is this one program that I always use in Windows, called InkLearn, that help me with learning Chinese and I have not found a Linux equivalent. I guess for now I have to wait for the next version of Ubuntu.

---

### Post by meierfra. on 2009-03-19
If you have a Ubuntu Live CD (or any other Linux Live CD) follow these instruction 

[How can I access my Wubi install and repair my install if it won't boot?]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won%27t%20boot?")


to run a file system check.

---

### Post by bapoumba on 2009-03-19
[http://ubuntuforums.org/showthread.php?p=6924335](http://ubuntuforums.org/showthread.php?p=6924335)
Here are the posts I moved from this thread. I also have edited one post here to remove inappropriate information.

---

