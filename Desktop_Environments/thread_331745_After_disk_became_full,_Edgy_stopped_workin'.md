---
title: "After disk became full, Edgy stopped workin'"
date: 2007-01-05
forum: Desktop Environments
---

### Post by sfunk1x on 2007-01-05
I was able to free about 600MB, then restart. MySQL had long since taken a dump, as well as most of apache. I know, I know, I should have kept tabs on it. It's an 80GB drive though.

So now, when I come to the login screen, I log in, and then it kicks me right back to the login screen. No visible error messages. I'm not an expert, so I'm not sure what to do in the recovery session. I'm currently searching, but so far nothing I've tried has worked.

I'd really hate to have to reinstall again, which would be a pita to setup all the mysql db's I need fo rwhat I do. Any suggestions?

---

### Post by coastdweller on 2007-01-05
Are you actually using the entire disk?

If you aren't then you can boot with a live cd and use GPARTED to expand, move the partitions around.

Not being able to do anything when out of disk space is perfectly normal.

---

### Post by sfunk1x on 2007-01-05
Actually, I have been trying to log in for the past 30 minutes, and I got an error message window that popped up. it said something along the lines of ' You are either out of disk space, or you are unable to write to the home directory because of permissions. '

Could this pc have been compromised in some way? It's running apache2, and some personal web stuff that I play with.

---

### Post by mcduck on 2007-01-05
Sounds more like too little disk space available for normal users. But no need to reinstall, just choose the safe mode from Grub menu to get in as root. (There is always 5% of disk space reserved for root only, just for cases like this). Then you can free some more disk space, and after that you should be able to log in again..

Running 'apt-get autoclean' should give you easily some free space by removing cached packages   (if you haven't done that already).

---

### Post by sfunk1x on 2007-01-14
This was actually a webmin problem. There was a logfile that grew, in a matter of 3 weeks, to over 68GB in size. Once that was deleted, everything was fine.

Thanks all!

---

