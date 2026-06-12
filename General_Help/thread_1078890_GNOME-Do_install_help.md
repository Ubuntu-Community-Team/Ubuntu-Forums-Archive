---
title: "GNOME-Do install help??????"
date: 2009-02-23
forum: General Help
---

### Post by SonnHalter on 2009-02-23
I added all the dependcies and everything but it still insists on installing an earlier version.


```
erik@ubuntu:~$ gedit
erik@ubuntu:~$ sudo aptitude install gnome-do
[sudo] password for erik: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  gnome-do-plugins 
The following NEW packages will be installed:
  gnome-do libevolution3.0-cil{a} libgnomedesktop2.20-cil{a} 
  libnotify0.4-cil{a} libwnck2.20-cil{a} 
0 packages upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 5956kB/6295kB of archives. After unpacking 9662kB will be used.
The following packages have unmet dependencies:
  gnome-do-plugins: Depends: libc6 (>= 2.9) but 2.8~20080505-0ubuntu9 is installed. or
                             libc6.1 (>= 2.9) which is a virtual package. or
                             libc0.1 (>= 2.9) which is a virtual package.
                    Depends: libgconf2.24-cil (>= 2.24.0) which is a virtual package.
                    Depends: libglib2.0-cil (>= 2.12.7) but 2.12.1-1ubuntu2 is installed.
                    Depends: libgnome-vfs2.24-cil (>= 2.24.0) which is a virtual package.
                    Depends: libgtk2.0-cil (>= 2.12.7) but 2.12.1-1ubuntu2 is installed.
                    Depends: libmono-posix2.0-cil (>= 1.0) which is a virtual package.
                    Depends: libmono-system2.0-cil (>= 2.0) but 1.9.1+dfsg-4ubuntu2 is installed.
                    Depends: gnome-do (>= 0.7.96~) but 0.6.1.0-0ubuntu2 is to be installed.
The following actions will resolve these dependencies:

Install the following packages:
gnome-do-plugins [0.6.0.1+dfsg-0ubuntu2 (intrepid)]

Score is 20

Accept this solution? [Y/n/q/?] 


```

---

### Post by Mud.Knee.Havoc on 2009-02-23
> **SonnHalter said:**
> 
Accept this solution? [Y/n/q/?] 
[/CODE]

So if you hit "Y", does it install?

---

### Post by frklin on 2009-02-24
Do You have repo from [https://launchpad.net/~do-core/+archive/ppa?](https://launchpad.net/~do-core/+archive/ppa?)

---

