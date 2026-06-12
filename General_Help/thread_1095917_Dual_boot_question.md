---
title: "Dual boot question"
date: 2009-03-14
forum: General Help
---

### Post by horax on 2009-03-14
Hidey ho,
I successfully installed Ubuntu on a second hard drive for dual bootability  with XP.  It works just fine...BUT...when I initially chose Ubuntu after the install, it gave me the following optoins:

Ubuntu xxxx-7
Ubuntu MemCheck
Ubuntu Safe Mode
Windows XP

Ever since that first startup, it now gives me the following options:

Ubuntu xxxx-7
Ubuntu MemCheck
Ubuntu Safe Mode
Ubuntu xxxx-11
Ubuntu MemCheck
Ubuntu Safe Mode
Windows XP

It seems as if it's picking up two separate installs of the SW...how could that be since I only installed it one time?

As I said in the disappearing HD thread, I cannot even access the Drive that Ubuntu is installed on to explore it's contents.  On my first access of teh system, I could  reach the Drive and everything.  But now, the drive is magically gone, and I cannot see it in either XP or Ubuntu.

What could possibly be going on?

I love the look adn feel of the OS and want to explore more, but if this issue is common, well, no wonder why people would be hesitant to change over to Linux.

Any help is appreciated.

Thanks!

hx

---

### Post by taurus on 2009-03-14
You don't have two installs; you just have two versions of kernels.

Boot into Ubuntu and post the outputs of these commands from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by horax on 2009-03-14
I will do that shortly.

What would give me two different Kernel builds from a single installation?

I uploaded and applied all of the software upgrades after the initial install, could this have updated my Kernel?

---

### Post by taurus on 2009-03-14
The system just upgraded your machine from an older kernel to a newer one.  There is no need to alarm about it.  You can remove the old kernel from synaptic if you wish or install startupmanager and use it to config how many kernels you want to keep on your machine.  You need at least one but better to keep a previous kernel too when installing a new one because if there is something wrong with the new one, you are a sitting duck if you don't keep an old one around.

---

### Post by jelle_ on 2009-03-14
it is common that every kernel upgrade means you get more kernels to boot in. this can be irritating, because you only boot in the most recent kernel. 
this is how you fix it:
1. boot into the ubuntu with the highest number
2. install KGRUBEditor from add/remove programs. this program let you remove the useless kernels
3. run KGRUBEditor and remove the ubuntu ending with -7-generic. don't change everything else!
4. open a terminal and type "sudo nautilus /boot" and remove everything ending with -7-generic

be careful when doing this! your computer can't boot anymore if you remove the wrong thing your computer can't boot

---

### Post by horax on 2009-03-14
Thanks for the tips! 

I will try this later today.

---

### Post by ajgreeny on 2009-03-14
Just uninstall the older unwanted kernel using synaptic.  The best way is to search using the kernel number, (2.6.27-7) and remove all of those if it really worries you.  Doing this will also remove references to the removed kernel from your grub menu.  I suggest you keep one older kernel that you know works, just in case.

Personally, I don't like and would not recommend the way of doing it suggested by jelle_, which is not the best way to remove a kernel or its allied packages and dependencies.  It will also need a number of kde (kubuntu) packages just to do what you can already do quite easily with a standard ubuntu system.

---

