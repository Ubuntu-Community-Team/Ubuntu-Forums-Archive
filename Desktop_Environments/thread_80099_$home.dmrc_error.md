---
title: "$home/.dmrc error"
date: 2005-10-21
forum: Desktop Environments
---

### Post by giopas on 2005-10-21
I guys, at boot,just before login, I receive this error, but I don't know what have I to do:
> your$home/.dmrc
Your has incorrect permissions and is being ignored. Thisprevents the default session and language from beeing saved. File should be owned by user and have 644 permission
I tryed to write: chmod 644 /home/giopas/.dmrc, but even if the change seems to take effect, at the following boot the problem come another time.

What have I to do? thnx

enjoy, ;)
giopas

---

### Post by Dr. Nick on 2005-10-21
I get this to, have gotten it for awhile, hopefully someone knows the fix right off hand, but I still am trying to get it fixed, If I find it out Ill post it here first

---

### Post by XDevHald on 2005-10-21
[QUOTE=Dr. Nick]I get this to, have gotten it for awhile, hopefully someone knows the fix right off hand, but I still am trying to get it fixed, If I find it out Ill post it here first[/QUOTE]
Goto the file where it's located, which would be in your /home/username and right click on it and goto **Properties**, then **Permissions** and set the owner to **Execute**.

---

### Post by XDevHald on 2005-10-21
[quote=Steve Myers]Goto the file where it's located, which would be in your /home/username and right click on it and goto **Properties**, then **Permissions** and set the owner to **Execute**.[/quote]

Adding to the above post, [http://ubuntuforums.org/showthread.php?t=16916](http://ubuntuforums.org/showthread.php?t=16916)

---

### Post by giopas on 2005-10-23
but... what about if I try to change permissions from a live cd? because the error message says: " your$home/.dmrc has incorrect permissions and is being ignored", so maybe when the system is on, it's disabled bydefault... :confused: 

when I find I live cd, I'll try it.

giopas

---

### Post by Bill Statler on 2005-10-23
Here's an explanation of the $HOME/.dmrc problem:

[http://www.ubuntuforums.org/showthread.php?p=437911#post437911]("http://www.ubuntuforums.org/showthread.php?p=437911#post437911")

But I don't know how this would work with the Live CD.

---

### Post by giopas on 2005-10-23
I tryed with live cd, but without success...

so, I tryed with the Bill's link and I did fixed. Thnx a lot!!!

enjoy, ;)
giopas

---

### Post by Dr. Nick on 2005-10-23
Chmod 700 /home/username worked like a charm. thanks. It put off a reinstall untill I severly screw up while testing dapper :)

---

### Post by housefly7k on 2008-06-23
```
sudo chown myusername /home/myusername
sudo chgrp myusername /home/myusername

```
and then 

```
chmod 700 /home/username
```

worked for me, thanks

---

### Post by ngohaibac on 2008-06-28
Hi housefly7k,

Thanks for your guide. It is work for me.

Best regards,

---

