---
title: "i've installed the LAMP server, now i want a light desktop...and firefox"
date: 2006-11-06
forum: Desktop Environments
---

### Post by bowie101 on 2006-11-06
hi all. after much tribulation , I've installed Dapper's Lamp server on an old laptop that has no internet connection to it. (I'm doing this for learning and testing.) 

I now want to install a light-weight desktop on it, as the computer is only 128mb RAM.... And then *firefox* and *bluefish* to enable editing and browsing of localhost. 

no internet connection for the computer in question, and what i'm on now is dial-up. 

the disks i have are: 

ubuntu dapper drake desktop cd, 
the server cd that i just installed, 
xubuntu dapper drake alternate install cd.

i thought i had xubuntu regular install of drake, but that image is no good.

do i have all i need? how do i proceed? hey, is there any documntaion on this stuff, as i sure don't see any!

---

### Post by JAwuku on 2006-11-06
If you want the Ubuntu Gnome desktop,

insert the Ubuntu Dapper cdrom, and type
```
[b]sudo apt-cdrom add
sudo apt-get install ubuntu-desktop[/b]
```

This allows you to install packages from the cd-rom without an internet connection.

If you want the Xubuntu Xfce desktop,

insert the Xubuntu Dapper cdrom, and type
```
[b]sudo apt-cdrom add
sudo apt-get install xubuntu-desktop[/b]
```

Hope this is useful

---

### Post by bowie101 on 2006-11-06
yes! it's  done! great!

---

