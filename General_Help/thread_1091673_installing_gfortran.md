---
title: "installing gfortran"
date: 2009-03-09
forum: General Help
---

### Post by tsachi on 2009-03-09
I am new user to linux. I tried to istall gfortran onto ubuntu 8.10
using the shell comands: 


admin@admin-laptop:~$ cd /home/admin/Desktop/gcc-trunk/bin
admin@admin-laptop:~/Desktop/gcc-trunk/bin$ sudo apt-get install gfortran
[sudo] password for admin:

the installation failed and returned the following error:

Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Couldn't find package gfortran


what am I doing wrong?

Best
Tsachi

---

### Post by taurus on 2009-03-09
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

p.s.  Did you remember to run **sudo apt-get update** first?

---

### Post by tsachi on 2009-03-10
for my reasons, I cant arrange an internet connection on my linux OS.
Can you explain to me how can I install gfortran onto ubuntu without an Internet conection?

Take into account that I am a total newby to linux.

Best
Tsachi

---

### Post by Yellow Pasque on 2009-03-10
First, make sure you have the build-essential package installed. I believe it's installed by default on 8.10, but don't quote me on that. If it's not installed, you can find it on your Ubuntu install CD.

Next, download gfortran 4-3 .deb from here: [http://packages.ubuntu.com/intrepid-updates/gfortran-4.3](http://packages.ubuntu.com/intrepid-updates/gfortran-4.3)
You also have to make sure the required dependencies are installed (and the required dependencies of those dependencies).

---

