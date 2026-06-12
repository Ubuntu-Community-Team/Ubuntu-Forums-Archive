---
title: "GDM startup scripts for Karmic?"
date: 2009-12-17
forum: Desktop Environments
---

### Post by mcfang on 2009-12-17
Prior to Karmic I used GDM startup scripts such as /etc/gdm/Init/Default for starting services such as synergy and x11vnc.

After upgrading to Karmic (Xubuntu) it appears these scripts are no longer run at startup, and I can't find which scripts I should be using.

---

### Post by krunge on 2009-12-17
You might want to put something like this:
```
touch /var/tmp/I_am_here
```
early on in /etc/gdm/Init/Default to make sure if it is being run or not (e.g. your other commands may be failing for other reasons.) If you see that file created (or its timestamp updated) you know the script is being run.

Also see this post where the fellow had a similar problem from upgrade 9.04 to 9.10:
[INDENT][http://ubuntuforums.org/showpost.php?p=8241566&postcount=12]("http://ubuntuforums.org/showpost.php?p=8241566&postcount=12")[/INDENT]
then read the rest of the thread (which admittedly goes all over the place..) for more details.

---

### Post by mcfang on 2009-12-17
Thanks, that thread held the solution: have to use PreSession/Default instead of Init/Default.

---

