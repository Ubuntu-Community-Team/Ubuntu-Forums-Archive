---
title: "misconfigured kernel"
date: 2012-04-21
forum: Desktop Environments
---

### Post by buttondup on 2012-04-21
Hi all
After having to do a fresh install of Ubuntu (11.10 Oneiric Ocelot this time) because of a failed hard drive :( I discovered that AMD cool'n'quiet was not working out of the box (perhaps because of my mobo?? and ACPI etc) Having it enabled in my BIOS always caused the system to hang pre and post installation.

It seems the wrong module was being inserted and looking at the kernel config it was not compiled with the necessary powernow-k8 support?!
So, I took the kernel source and recompiled (using the debian/ubuntu method) a custom kernel with many tweaks (some blind others more assuredly) but now when I boot this custom kernel there are many shortcomings, namely that I cannot use any package manager to install/uninstall and my chromium profile is error strewn. 
Using apt from the command line, I always get 


E: Could not get lock /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I know there are no other typical processes that may be causing the lock, it happens every time on reboot but not when I boot from the stock kernel.  

I suspect it has to do with security permissions and there is something I've missed in the kernelconfig but I can't fathom what (perhaps some obscure PAM requisite?)

Anyone have any pointers

I'm not that savvy but usually can home in on the root of problems with a bit of google assisted trial and error but this time I's stumped.
My thanks for your assistance.

---

### Post by buttondup on 2012-04-24
Bump

---

### Post by lisati on 2012-04-24
What happens when you run the following?
```
sudo apt-get update
```

---

### Post by buttondup on 2012-04-24
E: Could not get lock /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Also, CPU frequency scaling still does not work.

---

### Post by buttondup on 2012-04-24
I have discovered that when the CPU frequency is set to 1GHz I get the system hang.  All other frequencies are OK (I am using X2 6000+) By adjusting the minimum value using cpufreq-set I can the utilise the ondemand and conservative governors.
As for the other problem.....

---

