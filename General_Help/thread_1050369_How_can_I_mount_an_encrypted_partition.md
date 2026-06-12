---
title: "How can I mount an encrypted partition?"
date: 2009-01-25
forum: General Help
---

### Post by ruipedroca on 2009-01-25
Hi,

I've installed a new machine using the alternate ubuntu CD and following this tutorial: 
[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

But, during the installation, I didn't define a mount point for a partition I've created only for data. 

Now, I'm unable to mount it because the usual way in fstab doesn't work.

Can you help me?

---

### Post by mike2357 on 2009-01-25
Have you looked at the "encfs" command to mount your encrypted partition?  You can run
```
man encfs
```
for details

I use encfs for an encrypted directory.  A command somewhat like this might work, assuming you've created a directory for the unencrypted version of your encrypted partition as /mnt/sda3
```
encfs /dev/sda3 /mnt/sda3
```
encfs will then prompt you for your password.  If if all goes well, you can cd to /mnt/sda3 and read and write unencrypted versions.

When you're done, you can run reverse the mount with:
```
fusermount -u /mnt/sda3
```
Good luck.  As I mentioned, I have a encrypted directories rather than encrypted partitions like you have, so my suggestions might not work at all.

---

### Post by ruipedroca on 2009-01-27
Hi, mike2357

And if I want the OS to mount automatically at startup (fstab?...)?

---

### Post by mike2357 on 2009-01-27
Gee, I'm not sure.  Did the encfs and fusermount commands work for you?

I think that any way of getting the OS to mount your encrypted partition automatically would involve putting the password in clear text in a file in an unencrypted partition.  This would defeat your encryption strategy since anyone who got their hands on your hard drive could see the file and hence the password.

---

### Post by ruipedroca on 2009-01-28
It seems that encfs doesn't work with partitions because this is what resulted:

$ encfs /dev/sda3 /mnt/48gb   
The directory "/dev/sda3/" does not exist. Should it be created? (y,n)

(and, yes, /dev/sda3 is well defined, the partition/device is there in the /dev directory..)

Maybe I should just reinstall the SO and this time define a mount point to all partitions.
By the way, the root partition is encrypted (but not the boot one), so I think a text password wouldn't matter, would it?

Regards

---

### Post by mike2357 on 2009-01-28
ruipedroca, I'm sorry but I don't think I have the knowledge or experience to adequately help you, so I think it's best that I not speculate or I'll make things worse for you.  Maybe this will help you:

[https://help.ubuntu.com/community/FullDiskEncryptionHowto]("https://help.ubuntu.com/community/FullDiskEncryptionHowto")

---

