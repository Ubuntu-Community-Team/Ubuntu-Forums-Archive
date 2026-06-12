---
title: "where are linux-headers"
date: 2007-04-21
forum: Desktop Environments
---

### Post by mitjab on 2007-04-21
I want to install ati drivers but i can not find linux-headers-2.6.17-11-386 for my kernel?

Where i can find it in feisty?

---

### Post by jocko on 2007-04-21
If you use feisty you do not have a kernel version 2.6.17-11-386.
To get the headers for the default kernel, you simply install the package "linux-headers-generic", which will make sure the headers gets updated when the kernel is.
If you by any reason have chosen to install a different kernel (-386, -lowlatecy or -server) the name of the correct headers will be different.

---

### Post by mitjab on 2007-04-21
I have this version of kernel, i upgrade from edgy!

mitjab@ubuntu:~$ uname -r
2.6.17-11-386
mitjab@ubuntu:~$ 

So i must install different version of kernet that i will have linux-headers.

linux-headers-generic is alreday installed.

---

### Post by jocko on 2007-04-21
To get the headers for the edgy kernel you will have to install them from the edgy repos.

---

### Post by mitjab on 2007-04-21
ok thx did not know that.

Which is then feisty kernel?

---

### Post by Pobega on 2007-04-21
sudo aptitude install linux-headers-`uname -r`

That should do it.

---

### Post by mitjab on 2007-04-21
```

mitjab@ubuntu:~$ sudo aptitude install linux-headers-`uname -r`
Password:
Branje seznama paketov... Narejeno
Gradnja drevesa odvisnosti        
Reading state information... Narejeno
Reading extended state information      
Initialising package states... Narejeno
Building tag database... Narejeno      
No candidate version found for linux-headers-2.6.17-11-386
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Narejeno
mitjab@ubuntu:~$ 


```

still nothing

is it ok if i install kernel 2.6.20 and headers for it?

---

### Post by Pobega on 2007-04-21
Oh, right, I didn't read that you tried that already, sorry.

What is the outcome of "aptitude search linux-headers-"?

---

### Post by mitjab on 2007-04-21
no problem

```

mitjab@ubuntu:~$ aptitude search linux-headers-
v   linux-headers-2.6               -                                           
p   linux-headers-2.6.20-15         - Header files related to Linux kernel versi
p   linux-headers-2.6.20-15-386     - Linux kernel headers for version 2.6.20 on
p   linux-headers-2.6.20-15-generic - Linux kernel headers for version 2.6.20 on
p   linux-headers-2.6.20-15-lowlate - Linux kernel headers for version 2.6.20 on
p   linux-headers-2.6.20-15-server  - Linux kernel headers for version 2.6.20 on
p   linux-headers-2.6.20-15-server- - Linux kernel headers for version 2.6.20 on
p   linux-headers-386               - Linux kernel headers on 386               
p   linux-headers-686               - Obsoleted by: linux-headers-generic       
p   linux-headers-generic           - Generic Linux kernel headers              
p   linux-headers-k7                - Obsoleted by: linux-headers-generic       
p   linux-headers-lowlatency        - Low latency Linux kernel headers          
p   linux-headers-server            - Linux kernel headers on Server Equipment. 
p   linux-headers-server-bigiron    - Linux kernel headers on BigIron Server Equ


```

2.6.20 is in it, 2.6.17 not.

---

### Post by Pobega on 2007-04-21
sudo aptitude install linux-headers-generic linux-headers-386

Should work fine. If not, try installing a newer kernel and the kernel headers and see if that works.

---

### Post by jocko on 2007-04-21
> **mitjab said:**
> is it ok if i install kernel 2.6.20 and headers for it?

If you really have completely upgraded to feisty the 2.6.20 kernel should already be installed and be the default kernel.
I thought you had chosen to keep 2.6.17 by some reason.
If you don't have any reason to keep the 2.6.17 kernel I would advice you to make sure you have 2.6.20 installed:```

sudo apt-get install linux-generic linux-headers-generic
```
Then reboot and make sure to boot the 2.6.20 kernel (press Esc when grub loads to see the boot menu).
If everything works you should probably uninstall the 2.6.17 kernel.

---

