---
title: "Ubuntu crashes, but not as root"
date: 2008-09-16
forum: Desktop Environments
---

### Post by DPJB on 2008-09-16
Hi all,

I have several machines running Ubuntu fine. I've just installed it on a new machine (hardy, amd64) and have this weird issue i cannot figure out: When I normally boot the machine, it crashed just before or just after logging in. A total lockup.

However, if I choose the 'recovery' option, drop to a root shell, and run 'startx', I can Ubuntu for hours... no problems.

I guess the problem should be in one of the things loaded in multi-user mode, but not in single user mode... I'll have a look at that. But, in the mean time - Does anyone have a clue?

TIA,

Dirk

---

### Post by nowshining on 2008-09-16
disable compiz and see if that helps..

---

### Post by DPJB on 2008-09-16
Uninstalled compiz, but still the same thing...

---

### Post by nowshining on 2008-09-16
hmmm you could of just disabled..

do you perhaps overclock your videocard?? or even underclock?

---

### Post by DPJB on 2008-09-16
Well, not that I know... but X runs fine when started as root, trough recovery mode... Does it run any different than when started the normal way?

Cheers, Dirk

---

### Post by DPJB on 2008-09-16
Well, I also tried the Intrepid Beta, which basically does the same... :(

I guess I am one of the unlucky Hardy users on this paricular system...

---

