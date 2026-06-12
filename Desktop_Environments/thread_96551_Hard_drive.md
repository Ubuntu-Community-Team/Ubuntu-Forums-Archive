---
title: "Hard drive"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Blaauw01 on 2005-11-29
i forgot,

i have two hard drives but i am not able to write ( access ) the other hard drive.
( probably because i am not logged in as root).

I want to set up my hard drive as a path where a can save my data. How can i do that.

:(

---

### Post by dafl00 on 2005-11-29
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by bernardfrancois on 2005-11-29
maybe you can start with posting the output of **cat /etc/fstab** and **ls -l /mnt** (or replace */mnt* with the directory where you are mounting your partitions), also tell us which drive is the one where you don't get write access...

---

