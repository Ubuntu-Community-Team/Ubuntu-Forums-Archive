---
title: "No default root fs. Ubuntu 8.10 PS3"
date: 2009-03-27
forum: General Help
---

### Post by Mr_Chronic on 2009-03-27
Hi, this is my first post and unfortunately its a technical issue! Heres the problem, i downloaded ubuntu 8.10 and installed it following instructions from here [http://psubuntu.com/wiki/SetupPS3](http://psubuntu.com/wiki/SetupPS3).

But whenever i get onto the kboot screen  i get this error

Ubuntu PS3 KBoot Loader.
No default root fs was found, or one was found and it didn't contains a
message= config file.
If no rootfs was found, you can enter the shell here with 'sh'. Exiting
will return you to this prompt. In the shell you can mount your rootfs as
/mnt/root/.

Reasons this may have happened include:
 - No drive with a rootfs was actually found.
 - Your rootfs does not have the correct volume label of "/"
 - Your rootfs is corrups (use the rescue CD to fix this).

kboot: _

I really dont know how to fix this and any help will be appreciated.

I am an extreme linux noob so it would be helpfull if you could explain things in noob terms lol.

---

### Post by Pyrophosphate on 2009-05-23
I seem to be having exactly the same problem, and I have yet to find any way to fix it, so any help would be appreciated.

---

### Post by infocom on 2009-11-05
Did you find a fix for this, I get the same issue. 

Thanks

---

### Post by unit68 on 2010-05-21
instead of a guided install when it comes to the partitions do a manual install and select EXT3  NOT ext4  also may want a swap partition. hope this helps

---

