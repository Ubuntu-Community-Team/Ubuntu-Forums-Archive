---
title: "Unable to get linux headers"
date: 2009-04-26
forum: General Help
---

### Post by alec4rs on 2009-04-26
Hi, I'm a bit of a linux newb so please excuse me, I'm currently running Ubuntu 8.10 (I was on 9.04 but had to revert because the internet didn't work, couldn't dl package to fix it). My sound doesn't work (another issue) and i've gone through a series of problems, which all boil down to me updating my linux headers with :

```
alec@Prandpa:~$ sudo apt-get install linux-headers-`uname -r` 
```When I do this, I get :

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-headers-2.6.24-23-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-23-generic has no installation candidate

Because of this problem, I suspect, I'm unable to run ./configure (I was trying to install Alsa). Any suggestions?

---

### Post by kanikilu on 2009-04-26
Hmm, have you tried just **linux-headers-generic**?

---

### Post by xebian on 2009-04-26
> **alec4rs said:**
> Hi, I'm a bit of a linux newb so please excuse me, I'm currently running Ubuntu 8.10 (I was on 9.04 but had to revert because the internet didn't work, couldn't dl package to fix it). My sound doesn't work (another issue) and i've gone through a series of problems, which all boil down to me updating my linux headers with :

```
alec@Prandpa:~$ sudo apt-get install linux-headers-`uname -r` 
```When I do this, I get :

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-headers-2.6.24-23-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-23-generic has no installation candidate

Because of this problem, I suspect, I'm unable to run ./configure (I was trying to install Alsa). Any suggestions?

For 8.10, the kernel is at [COLOR="Red"]2.6.27[/COLOR]-xx-generic.  You are running an outdated kernel.

---

### Post by alec4rs on 2009-04-26
> **xebian said:**
> For 8.10, the kernel is at [COLOR=Red]2.6.27[/COLOR]-xx-generic.  You are running an outdated kernel.

How do I fix this?

Also, I tried ```
 	 	 	 	 	  sudo apt-get install **linux-headers-generic** 
```

it just returned: 

Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

