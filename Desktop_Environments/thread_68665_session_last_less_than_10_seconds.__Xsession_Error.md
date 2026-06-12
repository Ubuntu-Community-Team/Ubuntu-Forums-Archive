---
title: "session last less than 10 seconds.  Xsession Error Log"
date: 2005-09-23
forum: Desktop Environments
---

### Post by dysprosium on 2005-09-23
I have this issue occuring when I try to login.  I read the error log and apparently the gdm programs at login cannot launch as they don't have Permissions.  Any ideas?

---

### Post by mlomker on 2005-09-23
You'll need to post exact error messages if you want more than a wild guess.   :-P 

Generic advice would be to try **startx** and run a **dpkg-reconfigure xserver-xorg**.

---

### Post by cbudden on 2005-09-24
[QUOTE=mlomker]You'll need to post exact error messages if you want more than a wild guess.   :-P 

Generic advice would be to try **startx** and run a **dpkg-reconfigure xserver-xorg**.[/QUOTE]
 Had a similar error last night, error message said that something or other couldnt write to a directory on my /home folder.  Cured by a restart and apparently it was a disk error, and the fsck thingie (newb) fixed it.  Just follow what it says.

---

### Post by professor_chaos on 2005-09-24
I thought I was getting that message when using KDE applications in gnome and the permissions of .Xauthority were modified. 

Try logging on via commandline and type ```
ls -l .Xauthority
```
IF the ownership is not you or the permissions don't have read write, change them so.

---

