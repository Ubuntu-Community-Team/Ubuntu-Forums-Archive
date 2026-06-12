---
title: "Desktop effect cannot be enable (under vmware)"
date: 2007-10-27
forum: Desktop Effects &amp; Customization
---

### Post by victorw on 2007-10-27
Hi need help 

I am new with linux , please bear with me. 

Machine spec

AMD Athlon 3200 2.00 GHZ
RAM 1 gig
Video card nvidia geforce 6150

After I installed vmware in window xp and virtualise the ubuntu 7.10

I cannot turn on the Desktop effect and the error message that I get is 
"Desktop effect cannot be enable"

This thread suggested that installing vmware tools
[http://ubuntuforums.org/showthread.php?t=381938](http://ubuntuforums.org/showthread.php?t=381938)

and I did by following this tutorial 

[http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-eft/](http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-eft/)
 


thanks in advance

---

### Post by victorw on 2007-10-27
bump

---

### Post by mindtrick on 2007-10-27
You can't enable Desktop Effects in virtual machines as they have no support for 3d acceleration. You'll have to install it on a real partition for that.

---

### Post by victorw on 2007-10-27
CAn I install it with out killing my Xp ?

---

### Post by KhaaL on 2007-10-27
> **victorw said:**
> CAn I install it with out killing my Xp ?

Of course, the partitioner under the installation will ask you how it will install ubuntu, manually or automatically. after that it will install grub, so you can choose if you want to boot to ubuntu or windows.

I don't know if it's required, but just for safety defrag your windows drive before installing.

Good luck!

---

### Post by victorw on 2007-10-28
Thanks , I will try it when later ..

---

