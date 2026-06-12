---
title: "Trouble Compiling"
date: 2009-05-03
forum: General Help
---

### Post by cmpunk on 2009-05-03
Hi, I've been trying to install a driver for my built-in webcam in my compuer with Ubuntu 9.04. I've been having trouble compiling it: [http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?hl=en](http://groups.google.com/group/microdia/web/testing-microdia-driver-draft?hl=en)
Once I get to step two, I type in what it tells me to do, but it gives me an error:
E: Package linux-headers has no installation candidate

Anyone know what to do?

---

### Post by HermanAB on 2009-05-03
Howdy,

When I run into compile problems I take a crowbar and a sledge hammer to the problem and fix it good...

Install the kernel source and compile and install your own compiled kernel, reboot and then try to compile schtuff again.  Now you will find that all problems are gone.  You can Google for help or read this:
[http://aeronetworks.ca/kernel-compile-howto.html](http://aeronetworks.ca/kernel-compile-howto.html)

---

### Post by kayvortex on 2009-05-03
Try:
```
sudo aptitude install linux-headers-`uname -r`
```

Note that those are backticks (`), and not single quotes ('), and there are no spaces in "linux-headers-`uname -r`" except between "uname" and "-r". That should install the header files for your current kernel.

---

### Post by cmpunk on 2009-05-03
i ran the code you told me to do. all i got was this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kernel-package is already the newest version.
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.28-3-rt 2.6.28-3.12
  linux-ports-headers-2.6.28-6 2.6.28-6.20
  linux-headers-2.6.28-6-386 2.6.28-6.20
  linux-headers-2.6.28-11-server 2.6.28-11.42
  linux-headers-2.6.28-11-generic 2.6.28-11.42
  linux-headers-2.6.28-11 2.6.28-11.42
You should explicitly select one to install.
E: Package linux-headers has no installation candidate

```

And i already tried to install each of the packages it tells me in the code above. is it an issue with my package manger. do i need to enable anything in my package sources? by the way, i just installed 9.04

---

### Post by kayvortex on 2009-05-04
Right, after poking around on my own computer, I've come to the hypotheses (correct me if I'm wrong) that you're using apt-get instead of aptitude. The two do the same thing, but aptitude is safer. Whenever you see apt-get, it's safe (and highly recommended) to replace that command with aptitude.
Based on the assumption that you're using apt-get, it will complain about virtual packages (linux-headers is not a real package, it just points to the package linux-headers-2.6.whatever); aptitude doesn't have this problem.
So, could you confirm the exact command you are entering, and what the output of that command is.

---

