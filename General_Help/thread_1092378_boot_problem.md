---
title: "boot problem"
date: 2009-03-10
forum: General Help
---

### Post by steeler on 2009-03-10
hi.. i after making my linux partition bigger with gparted i restarted the pc and booted successfuly.but after like 20 min using linuxdc++ disc activity went up very high..KDE crashed and i had to reset the pc..now every time i try to log in disc activity boosts for 10 min or so until kde crashes..any help appreciated..

---

### Post by prince_niceguy on 2009-03-10
can you check which process is taking the highest time or disk usage. please use top command for doing that. should give some idea what is the issue. partitioning should not create such problems. also run fsck for ensuring that file system is consistent, gparted should have done that already but it does not harm doing it.

---

### Post by steeler on 2009-03-10
i've run fsck and everything is fine..
i can hardly move the mouse so running top would be somewhat difficult.will try anyway.a log might also be useful.

---

### Post by prince_niceguy on 2009-03-10
press ctrl + alt + F1, will take you to a login terminal, now login and do a top there, should work as this is a kind of alternate terminal without X loaded in it.

---

### Post by steeler on 2009-03-11
ok..i run top.and top processes are plasma, kde4, apt-cache, knotify and swapd0. cpu usage isn't higher than 10% or 15% any given time. but ocassionaly it prints "Out of memory: kill process xxxx (kdeinit)" (maybe other processes too, just think this one's more important). I barely have 256 of RAM but i haven't had any problems in the past.

---

### Post by plucky on 2009-03-11
Did you make any changes to your swap partition?

Post output of ```
free -m
cat /etc/fstab
sudo blkid
```

---

### Post by steeler on 2009-03-12
uuid of swap partition doesn't match the one listed in fstab..so i guess this is the problem.perhaps gparted formatted swap instead of moving it.thank you.

but i have one more question (kinda out of topic)
after successfuly logging in i run free -m and it indicates that only 6mb out of 256 of physical memory is free. is this normal? what processes could i disable in order to increase it?

---

### Post by plucky on 2009-03-12
> after successfuly logging in i run free -m and it indicates that only 6mb out of 256 of physical memory is free. is this normal? what processes could i disable in order to increase it?

That is normal as linux tries to utilize as much memory as possible as it is quicker to cache data in memory rather than have to fetch it from disk or swap area.


Good Luck

---

