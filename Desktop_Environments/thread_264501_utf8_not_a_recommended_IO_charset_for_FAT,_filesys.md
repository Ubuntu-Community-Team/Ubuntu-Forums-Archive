---
title: "utf8 not a recommended IO charset for FAT, filesystem will be case-sensitive"
date: 2006-09-24
forum: Desktop Environments
---

### Post by ropers on 2006-09-24
Hi, 
I am using Ubuntu Dapper Drake 6.06 LTS.
I have the following line in my /etc/fstab:

/dev/hdc1       /mnt/fattie     vfat defaults,umask=0222,rw,user 0    2

This is a FAT32 partition from Windows XP, which I can mount ok.
However, upon boot it says at the end of my dmesg:

[17179647.740000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

I am aware that many users/previous posters appear happy to ignore that message, given that they can read/write to the partition. I however would like to ensure that this partition --which is obviously case-insensitive under Windows XP-- is also case-sensitive under Linux. I know that this could only ever bocome a problem if I/some application really created to eponymous files with different capitalization on that partition, but nevertheless I would like to know how this issue can be resolved. I'm especially stumped as I believe that Windows XP uses UTF-8, so I don't see how I could specify something other than UTF-8. I also don't see what the codepage/character set/use of Unicode has to do with file system case sensitivity. 

Any ideas?

Many thanks in advance,
--ropers

---

### Post by ropers on 2006-09-24
I have to amend my previous post:
I previously actually had two case-sensitivity error messages in my dmesg, but I've now changed my /etc/fstab and that previously quoted line now says:

/dev/hdc1       /mnt/fattie     vfat    user,auto,uid=ropers,gid=ropers,fmask=0111,dmask=0000   0 2

This results in no case-sensitivity error messages in the dmesg.
However, when I attach a USB flash drive/keyfob, I do get the same error message again. 

So: 
I don't think *both* previous error messages were related to the USB drive; I'm only getting one in relation to it now. I don't understand why I got one of these error messages in relation to the hdc1 FAT32 partition before. I also don't understand why I'm now no longer getting that one.

I don't think it's "right" that I'm getting that error message with the flashdrive now -- or rather I think I'm having a problem with unwanted case sensitivity there. A test confirmed that I can indeed create a "New file" and a "new file" on the FAT partition on the flash drive. I feel that with FAT32 partitions case-insensitivity should definitely be the default. There would be very few circumstances where users would expect and want a FAT32 partition to be case sensitive. It never is in Windows AFAIK, and that --for better or worse-- sets the standard here since FAT32 is really a MS partition format. Also, what I wrote about the character set -- that it shouldn't matter here, that also still applies.

While this may be Ubuntu's default automounter behaviour now: Nevertheless, what do people make of this? Is this stuff fixable?

---

### Post by dcstar on 2006-09-25
> **ropers said:**
> 
......
While this may be Ubuntu's default automounter behaviour now: Nevertheless, what do people make of this? Is this stuff fixable?

I believe you can change the default setting when you compile a kernel:

[http://www.linuxfromscratch.org/lfs/view/development/chapter08/fstab.html](http://www.linuxfromscratch.org/lfs/view/development/chapter08/fstab.html)

So perhaps the Ubuntu developers may want to look into this with the default kernels they compile? (you may have to lodge a bug report to bring it to their attention).

---

### Post by ropers on 2006-09-25
Thanks for this. I have now logged this bug report:

[https://launchpad.net/distros/ubuntu/+bug/62321](https://launchpad.net/distros/ubuntu/+bug/62321)

All the best,
--ropers

---

