---
title: "Automatically Mount Internal VFAT Partition on Startup"
date: 2009-05-18
forum: General Help
---

### Post by jjcobm on 2009-05-18
Hi everyone,

I just got jaunty installed on my laptop and I love this.  I got everything set the way I want it except for one thing that I can't figure out. I would like my internal Fat32 partition to mount automatically with Ubuntu on startup with full read and write permissions.

I tried play around with the /etc/fstab file using these options:

> #Backup Drive
UUID=4A00-011F /media/Backup vfat user,rw,umask=000 0 0

I did get the drive to mount at startup using this, but when I try to delete a file it says I don't have permission.

I would really appreciate if someone can help me out and possible explain what I am doing wrong as I am trying to learn as much as I can about this operating system.

Thank you!

---

### Post by Locutus_of_Borg on 2009-05-18
set the uid and gid of your user in the options section

```
user,exec,uid=1000,gid=10
```

something like that i think should do it

---

### Post by jjcobm on 2009-05-18
Thank you, I just set the "uid" to my user which was 1000 like you said and it worked perfectly.

Is it still necesarry to add the gid section?  I looked into it and a gid=10 would equal to UUCP group in my /etc/passwd file.  I am not sure what group this is or if this option is needed at all though?

---

