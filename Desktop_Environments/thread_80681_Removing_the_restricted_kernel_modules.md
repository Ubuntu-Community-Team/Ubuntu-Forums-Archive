---
title: "Removing the restricted kernel modules"
date: 2005-10-22
forum: Desktop Environments
---

### Post by idn on 2005-10-22
I need to remove the restricted kernel modules, [see this post]("http://www.nvnews.net/vbulletin/showthread.php?p=726214#post726214")

But it also wants to remove linux-386, should I do this?

---

### Post by Mizzou_Engineer on 2005-10-22
If you don't want to use restricted modules, why not recompile the kernel? That cannot use the restricted modules from what I was told. 

Also, I am sure that you have a computer than can run linux-686, why not try to install that and then get rid of linux-386. The 686 kernel should perform better anyway, it does for me.

---

### Post by idn on 2005-10-23
Yeah i have aan AMD64x2, but the thing is I want to use 32bit linux because of the better application suppport, I'm not sure if I can use the 64bit kernal and 32bit linux

---

### Post by Kyral on 2005-10-23
I don't know if running a 32-bit kernel on 64 bit would work...in theory it should, but I haven't heard of it happening. 

As for the NVidia Module. sudo apt-get install nvidia-glx

---

### Post by idn on 2005-10-23
No, I want to remove that module from the kernal :) It may be the reason why the latest nvidia driver wont install

---

