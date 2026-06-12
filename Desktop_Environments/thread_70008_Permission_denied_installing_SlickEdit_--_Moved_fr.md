---
title: "Permission denied installing SlickEdit -- Moved from Other App Support"
date: 2005-09-28
forum: Desktop Environments
---

### Post by hawkeye1315 on 2005-09-28
Hello all,
I am having difficulty in getting Visual SlickEdit IDE on my laptop. The software comes on a CD and has an installtion binary called vsinst under linux/x86. So, after inserting the CD, it is mounted automatically on /cdrom. So I cd /cdrom/linux/x86 and then sudo ./vsinst. Problem is I get "Permission Denied".  I also tried activating the root account (sudo su - passed) with the same results. Can anyone shed light on the problem? Thanks in advance.

Please let me know if I've omitted any pertinent info.

HK

---

### Post by KingBahamut on 2005-09-28
Move the binary to your local machine and try again. 
Be sure you chmod it to 0755 or something.

---

### Post by hawkeye1315 on 2005-09-29
Thanks Bill, that worked! Don't know why I didn't think of that earlier. But I am here to learn, can you tell me if this is a "security" feature of Ubuntu - to not allow execution of binaries from the cdrom? Thanks

---

### Post by KingBahamut on 2005-09-29
Thats something intrinsic to the physics of a cdrom.

---

### Post by pelago on 2005-09-29
[QUOTE=KingBahamut]Thats something intrinsic to the physics of a cdrom.[/QUOTE]
There's nothing in the physics of a CD-ROM which would stop you executing a program off it.

---

### Post by KingBahamut on 2005-09-29
No, but if the umask is set to 0000 in /etc/fstab for that cdrom/dvd/optical device , then it makes anything on the cdrom not executable. I think defaults in that file makes this permission set as well. Could be wrong though.

---

