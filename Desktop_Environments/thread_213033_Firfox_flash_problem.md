---
title: "Firfox flash problem"
date: 2006-07-10
forum: Desktop Environments
---

### Post by mech7 on 2006-07-10
> chris@acerChris:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree... Done
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-nonfree has no installation candidate
chris@acerChris:~$ sudo update-flashplugin
sudo: update-flashplugin: command not found


[http://ubuntuguide.org/wiki/Dapper#General_Notes](http://ubuntuguide.org/wiki/Dapper#General_Notes)

It does not work like it says on the page :(

---

### Post by reacocard on 2006-07-10
try enabling universe and multiverse: [https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by aysiu on 2006-07-10
Also, remember that after you enable extra repositories, you need to get them recognized (updated) before you can use them: ```
sudo aptitude **update**
sudo aptitude install flashplugin-nonfree
```

---

