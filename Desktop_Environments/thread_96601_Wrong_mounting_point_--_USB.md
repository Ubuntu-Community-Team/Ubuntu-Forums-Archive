---
title: "Wrong mounting point -- USB"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Jagunço on 2005-11-29
Hi folks.
I just installed Kubuntu 5.10, and noticed that when I plug my USB pendrive a Konqueror window appears and points to /dev/sdc (I don´t remember for sure), showing nothing. The pendrive is mounted at /media/PENDRIVE and is fully functional, but I´d like to know how to fix this problem.
Sorry for the poor english.
Greetings.

---

### Post by seppo on 2005-11-29
what does "mount" say? 
It should contain a line like this: 
/dev/sdc on /media/sdc type vfat (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8) 

You could add a line to /etc/fstab so that your pendrive is mounted at a fixed point. 

Do I satisfy your question?

---

### Post by GeneralZod on 2005-11-29
Firstly, make sure that your system is 100% up-to-date; there were a lot of bugs in the Kubuntu initial concerning Konqueror popping up opened to entirely the wrong URL when removable media was inserted which have since been fixed.

---

