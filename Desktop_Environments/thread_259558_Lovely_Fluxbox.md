---
title: "Lovely Fluxbox"
date: 2006-09-17
forum: Desktop Environments
---

### Post by Kelpie on 2006-09-17
On my way to installing fluxbox on the new version of Ubuntu... I get a lovely error. I try to figure how to fix it by reading through the forums, however my problem seems to not be resolved by this.

How my setup is:

Right now, I'm using 6.06 x86 under VMWare. I don't think I'll try x64 for now, it seems too fresh for me. I don't know if running it under VMWare can effect anything, but I would believe it shouldn't.

I feel like I should go back to 5.10, because I really liked it better. In my opinion 6.06 just seems so dumbed down that it's too dumbed down. But that is just my opinon. Now onto my problem:

I have of course followed the 6.06 backports, installed and updated essential things, however, when trying to install fluxbox, I get a tiny problem. Perhaps it's named different, perhaps not. But I did follow other threads and the problem wasn't solved:


Even [https://help.ubuntu.com/community/Fluxbox]("https://help.ubuntu.com/community/Fluxbox") can't solve my problem.

When trying to do as told in the terminal under root I get the following problem:

```

root@amber-vmware:/home/amber# aptitude install fluxbox
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "fluxbox"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


Or

When trying someone else's way:


root@amber-vmware:/home/amber# aptitude install fluxbox fluxboxconf
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "fluxbox"
Couldn't find any package whose name or description matched "fluxboxconf"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.




```

I would really like to beable to use fluxbox, but it seems next to impossible for 6.06.

And if you want to see what I have for my source list:


```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe


```

---

### Post by jrib on 2006-09-17
You don't have dapper universe enabled.  [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories) should have instructions for enabling universe.

---

### Post by Ramses de Norre on 2006-09-17
Add ' universe multiverse' to the first line, you'll then be able to install fluxbox.
I have it installed on dapper and it runs very smooth;)

---

