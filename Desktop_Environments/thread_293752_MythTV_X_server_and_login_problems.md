---
title: "MythTV X server and login problems"
date: 2006-11-05
forum: Desktop Environments
---

### Post by bigdave146 on 2006-11-05
Hello

I am running the latest 6.06LTS release and have followed the readme [here]("http://www.mythtv.org/wiki/index.php/Ubuntu_Dapper_Installation") to install and configure MythTV.

All is good up to the point where i have to log in as the mythtv user.  The login is OK but i cannot start any programs.  e.g., if i try to launch a terminal or anything else i get the busy icom and then nothing appears.

Also, if I run "sudo mythtv-setup" i get the error "mythtv-setup: cannot connect to X server".  I suspect the two problems are related.  I ran "sudo strace -f  mythtv-setup" and from the output there are alot of entries like...

access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)

I dont know if this is the cause, but I also dont know how to fix it as I have followed the install guide to the letter !!!

Help !!!

Dave

---

### Post by bigdave146 on 2006-11-07
Anyone ?

Dave

---

### Post by superm1 on 2006-11-07
Dave,

Its a bit ambiguous when you say that you have followed the guide to the letter.  That guide you used claims to be incomplete, and at first glance has the user going several different routes within the guide.

Are you able to actually run X apps?  Example, xterm, or firefox.

---

