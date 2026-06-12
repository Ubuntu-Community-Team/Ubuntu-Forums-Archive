---
title: "xserver doesn't start Ubuntu 9.04 x64"
date: 2009-05-30
forum: General Help
---

### Post by alchi on 2009-05-30
Hi!
When my Ubuntu starts, it says that there is an error and xserver cannot be loaded.
I cannot find any tracks of error in syslog though.
When I tried "sudo dpkg-reconfigure xserver-xorg", it said that file is read-only.
I can't edit xorg.conf, because I don't have access to it, even through "sudo".
I tried recovery mode --> root shell, but it still says that files are read-only, and I cannot modify them. 
But ls -l xorg.conf gives
-rw -r- -r- root root ...

I installed this system 3 days ago. It worked perfect until today.
I have the same OS on my desktop, it works fine.

Laptop's specs:
Model: Lenovo 3000 N200-0769
Dual boot OS: Ubuntu 9.04 x64/ Vista SP1 x32
CPU: Intel Core Duo 2Ghz
RAM: 4GB
HDD: 250 GB
Video: Geforce 7300 Go

Any ideas?

---

### Post by mrog on 2009-05-30
In /etc/group is your user name listed as a member of the admin group?

---

### Post by alchi on 2009-05-30
id username
groups=4(adm),121(admin), etc.

cat /etc/group | grep username
adm : x : 4 : username
admin : x : 121 : username
etc

So, yes

P.S. 
I tried booting from live cd and editing xorg.conf by changing driver to vesa, but it didn't work :(

---

