---
title: "I dont wanna start xorg when booting"
date: 2005-08-16
forum: Desktop Environments
---

### Post by odin on 2005-08-16
Hi!!

I need to use kernel 2.4.18 with some patches and when I boot with it every thing looks fine but the x configuration.It says something like " xserver is for kernel 2.6.x" so I would like to boot on text mode when I boot with this kernel.Is there anyone that could guide me on how to do this? what do I have to change?

Is there any other way of solving this problem? I really need to get this problem solved or my boss will never trust me about using linux for anything else!!!!!  ;-) 


Thank's in advance

---

### Post by heimo on 2005-08-16
[left]
Enable universe:
[https://wiki.ubuntu.com/UniversePackages]("https://wiki.ubuntu.com/UniversePackages")

Install rcconf
 ```
sudo apt-get install rcconf
``` 
Run rcconf:
 ```
sudo rcconf
``` 

disable gdm. Or just uninstall gdm and all the other desktop stuff, if those are not needed.

EDIT: Or... something like this, unverified
sudo mv /etc/rc2.d/S19gdm /etc/rc2.d/K19gdm
sudo /etc/init.d/gdm stop




[/left]

---

### Post by odin on 2005-08-17
Thank you very much,the rcconf worked fine.

But now I can see that in the directory /lib/modules I dont know why every time I compiled a new kernel there's nothing for that kernel and is giving me probelms when I'm trying to install things.

What am I doing wrong? is there any how to compile the 2.4.x kernel so I can see the problem?

---

### Post by heimo on 2005-08-17
Did you install modules?

This should be possible with vanilla sources too:
[http://www.ubuntuforums.org/showthread.php?t=56835](http://www.ubuntuforums.org/showthread.php?t=56835)

If you're following the more generic, "old-school" method, don't forget to run *make modules-install*

---

### Post by odin on 2005-08-17
I installed the modules and about doing it in the deb/ubuntu way I just cannot because I need kernel 2.4.18 and I couldnt find it in the repos.

---

### Post by heimo on 2005-08-17
You can take the same source files and use the methods in post linked above.

If using the old method: Pay attention to the part where modules are copied, unless you're compiling _everything_ into the kernel, you should obviously have modules under /lib/modules/.

---

