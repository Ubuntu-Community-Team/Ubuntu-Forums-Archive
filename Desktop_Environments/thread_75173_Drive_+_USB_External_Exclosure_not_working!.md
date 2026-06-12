---
title: "Drive + USB External Exclosure not working!"
date: 2005-10-13
forum: Desktop Environments
---

### Post by tofu1 on 2005-10-13
Help! I wanna install Breezy, but I can't without backing up my 3gb of stuff! Just plugging in my USB hard drive worked before, but now it's not working!

Hotplug is running ok.

Mount shows:
root@wind:/home/kevin # mount
rootfs on / type rootfs (rw)
/dev2/root2 on / type ext3 (rw)
proc on /proc type proc (rw,nodiratime)
sysfs on /sys type sysfs (rw)
/dev2/root2 on /.dev type ext3 (rw)
none on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw)
tmpfs on /dev/shm type tmpfs (rw)

I know it's /dev/sda1 but I don't know how to mount it...

//edit: Okay, it's not even mounting my CFcard plus USB reader. Strange. Help!! I want Breezy!! Lol

---

### Post by aysiu on 2005-10-13
Isn't the syntax usually something like this? ```
mount -t vfat /dev/sda1 /mnt/backupkey
```

---

### Post by tofu1 on 2005-10-13
Okay it says 

mount: can't open /etc/mtab for writing: Input/output error

Help!

---

### Post by aysiu on 2005-10-13
I know this is a bit discouraging to hear, but when [a Google search for your error](http://www.google.com/search?hl=en&q=%22mount%3A+can%27t+open+%2Fetc%2Fmtab+for+writing%3A+Input%2Foutput+error%22&btnG=Google+Search) turns up only 21 results, you may not find your solution any time soon.

Anyone else know what this is?

---

