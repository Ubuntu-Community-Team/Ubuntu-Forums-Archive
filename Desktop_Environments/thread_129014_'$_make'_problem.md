---
title: "'$ make' problem"
date: 2006-02-12
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-02-12
When trying to compile a package I always get the same kind of error when I say make: ```
ramses@icarus:~/Desktop/spca5xx-20060202$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/ramses/Desktop/spca5xx-20060202 CC=cc modules
make: *** /lib/modules/2.6.12-10-k7/build: No such file or directory.  Stop.
make: *** [default] Error 2

```
Anyone an idea what I can do about this?
The build file of which he says it is missing was created just before executing make..

---

### Post by taurus on 2006-02-12
Are you sure /lib/modules/2.6.12-10-k7/build is pointint to the same version of your kernel source (or headers) in /usr/src/???

---

### Post by Gandalf on 2006-02-12
```
apt-get install kernel-headers-`uname -r`
``` should fix it

---

### Post by Ramses de Norre on 2006-02-13
```
ramses@icarus:~$ sudo apt-get install kernel-headers-2.6.12-10-k7
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-headers-2.6.12-10-k7
ramses@icarus:~$ uname -r
2.6.12-10-k7

```
What repo should it be in?
And I checked the sym link, seemed ok to me..

---

### Post by kaamos on 2006-02-13
should be
```
sudo apt-get install linux-headers-$(uname -r)

```

---

### Post by Ramses de Norre on 2006-02-13
I'm gettin another error now.. I'm trying to install the scpa5xx driver.
```
ramses@icarus:~/Desktop/spca5xx-20060202$ sudo insmod spca5xx.ko
insmod: error inserting 'spca5xx.ko': -1 Invalid module format

```
They say in the how to that I should download the kernel I'm using? What do they mean with that?

---

### Post by Gandalf on 2006-02-13
You are confusing what is $(uname -r) it is not meant to be replaced manually, everything between $() or `` will be used as a command and the result of it will be treated by bash in your case it will be replaced by your uname -r

anyway type
```

apt-cache search kernel-headers

```
and install the one that matches your kernel...

---

### Post by kaamos on 2006-02-13
Gandalf: there is no kernel-headers versioning. The package used to get the headers is linux-headers
> alaisi@ubuntu:~$ apt-cache search kernel-headers
kernel-package - A utility for building Linux kernel related Debian packages.
linux-kernel-headers - Linux Kernel Headers for development
comedi-source - Comedi kernel module source
dvb-dev - Dummy package for upgrade purposes only
rt2400-source - RT2400 wireless network drivers source
rt2500-source - RT2500 wireless network drivers source
ipw2100-source - source for the ipw2100 driver

At least in breezy that is.

---

### Post by Ramses de Norre on 2006-02-13
I changed the stupid post above with a new problem appearing.. just making sure you'd read it:) thx;)

---

### Post by Ramses de Norre on 2006-02-14
anyone a solution? (it's a messy thread, the problem is 4 posts above..)
I'd really like to be able to compile from source but I hasn't been succesful yet..

---

### Post by Ramses de Norre on 2006-02-14
found solution
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

---

