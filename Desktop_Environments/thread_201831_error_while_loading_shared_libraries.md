---
title: "error while loading shared libraries:"
date: 2006-06-22
forum: Desktop Environments
---

### Post by chajuram on 2006-06-22
Hi,

I am having a problem running a particular program (TreeLD from [http://pritch.bsd.uchicago.edu/treeld.html)](http://pritch.bsd.uchicago.edu/treeld.html)). I compile the program and when I try to run I get the error 
> ./treeld: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory


So I tried looking for libstdc++-libc6.2-2 on our repos and then on google, but could not get anything. I will be very grateful if anyone could help me find the package.

Chajuram.

---

### Post by Ramses de Norre on 2006-06-22
It's something like this you need: (check for the names with aptitude search, I'm not on ubuntu now)```
sudo aptitude install libstdc++6 libstdc++6-0-dev
```

---

### Post by chajuram on 2006-06-23
Hi Ramses,

Thanks for your post.

I installed the following packages 
libstdc++6 and libstdc++6-dev
which were the closest to the names you suggested, but I still get the same error.

Chajuram.

---

### Post by darkultra on 2006-10-30
I have similar problem when I run vncviewer. I have just upgraded to edgy, and i can't find libstdc++ or libc6.2-2.so.3 in System - Administration - Synaptic Package Manager. 
```

starfleet@zippo:~$ vncviewer
vncviewer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: canno
t open shared object file: No such file or directory
```

---

### Post by Darkmoon_UK on 2007-05-24
I have the same issue. Are these important libraries and are they missing from (K)ubuntu?

---

### Post by dcjordan1 on 2007-06-12
If you get an error like this one on Ubuntu,

error while loading shared libraries: libstdc++-libc6.2-2.so.3:
cannot open shared object file: No such file or directory

it means the library isn’t available and you need to install it. Although the Ubuntu package which contains this library isn’t obvious. You can install it via the following command:

sudo apt-get install libstdc++2.10-glibc2.2


this worked for me.

---

### Post by sk8dork on 2007-06-23
> **dcjordan1 said:**
> If you get an error like this one on Ubuntu,

error while loading shared libraries: libstdc++-libc6.2-2.so.3:
cannot open shared object file: No such file or directory

it means the library isn’t available and you need to install it. Although the Ubuntu package which contains this library isn’t obvious. You can install it via the following command:

sudo apt-get install libstdc++2.10-glibc2.2


this worked for me.

i had this problem when trying to run RTCW multiplayer. the steps in the quoted post fixed it. thanks.

---

### Post by crazedgremlin on 2007-07-31
You're all so awesome!  Now I can play N, aka "the ninja game!"

[http://www.harveycartel.org/metanet/downloads.html](http://www.harveycartel.org/metanet/downloads.html)

---

### Post by Scorpuk on 2007-10-22
I have the same problem with realvncviewer and tried the above fix, but got this error:

```
john@Server:~$ sudo apt-get install libstdc++2.10-glibc2.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++2.10-glibc2.2
john@Server:~$ 

```


Anyone?

---

### Post by resole83 on 2008-07-17
> **Scorpuk said:**
> I have the same problem with realvncviewer and tried the above fix, but got this error:

```
john@Server:~$ sudo apt-get install libstdc++2.10-glibc2.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libstdc++2.10-glibc2.2
john@Server:~$ 

```


Anyone?

try sudo apt-cache search libstdc

For the "error while loading shared libraries..."

Before to install (it it's really necessary..) try to locate it in /

$ sudo find / -name "lib_name"

If you find it and it isn't in the /usr/lib folder..

$sudo cp _where_you_find_the_lib /usr/lib
$sudo ldconfig

...and try to recompile!

:guitar:

---

