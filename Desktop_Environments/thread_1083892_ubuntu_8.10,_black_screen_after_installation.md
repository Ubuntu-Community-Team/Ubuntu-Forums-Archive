---
title: "ubuntu 8.10, black screen after installation"
date: 2009-03-01
forum: Desktop Environments
---

### Post by zmagic on 2009-03-01
I successfully installed ubuntu 8.10. But when I log in with my username and password, I get a black screen. I can move the mouse around but I can't do anything. Prior to this installation I had ubuntu 7.04 installed without any problems. I even tried to install 7.04 back, but I had problems doing that as well. I don't remember what problem I had when reinstalling 7.04 but the 8.10 is definitely the black screen issue. Someone please save me from this frustration!!!!!!!!!!!!!!!

---

### Post by valkyrk on 2009-03-01
I'm experiencing exactly the same issue after a clean install after running Gutsy on this computer for a long time successfully. I initially tried to install with / , /home and swap partitioned, thought that might be an issue so allowed install on whole drive, but with same result.

---

### Post by Sysero on 2009-03-02
Hey,

I've seen a solution to this somewhere on here, (just where I can't recall) that has worked for some people.

Reboot your computer.  After GRUB loads the selection menu, choose the option with the word "Recovery" in it.  Should be the second menu option from the top.

From there choose the selection that sends you to root and type the following:

```
sudo apt-get purge compiz compiz-core
```

After that reboot and see if things work.  Meanwhile, I'll look around for the thread about this problem.

---

### Post by sahabcse on 2009-03-02
Hi

Login to the Terminal mode, Press ctrl+alt+F1 and enter the user name and password. Or login to the single user mode. Try to restore x and start the X.

---

### Post by Sysero on 2009-03-02
> **Sysero said:**
> 

Meanwhile, I'll look around for the thread about this problem.

Here's that link to that thread I was talking about.  

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=984296]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=984296")

Look at post #7 and #10 and also check out pages two and three in case it doesn't work.

---

