---
title: "problems with kernel sources"
date: 2005-12-17
forum: General Help
---

### Post by fallen on 2005-12-17
Hello,

I'm trying to get ALSA on my laptop, but here is the problem I have run.
When trying to configure alsa-drivers:
./configure --with-oss=yes --with-card=hda_intel --with-kernel=/usr/src/linux-source-2.6.12

everything goes smoothly until:
[PHP]
checking for directory with kernel source... /usr/src/linux-source-2.6.12
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux-source-2.6.12/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
[/PHP]


well strange, I have apt-get'ed the kernel sources everything is in place, but how can it be missing the version.h file?
I have created that file, then tried and got another problem, again file not found.

Have no idea what can be wrong :/

I use:
Kubuntu breezy
kernel 2.6.12

maybe anyone else had similar problem and can share their thoughts?

Thnaks in avance,
Fallen

---

### Post by stuporglue on 2005-12-17
First, why do you need to install alsa? The stock kernel's support alsa on a lot of devices.You may be able to avoid the whole compliation thing entirely. 


Second, what kernel are you running, and did you install it's header package?
Edit: Sorry, it's way too late. I should have seen your kernel version already. What'd you apt-get to get the kernel sources, it needs to be the same version as you're running, I think.

---

### Post by fallen on 2005-12-17
Yes I do have the same version of the sources as the kernel running.
headers too.

Old alsa drivers do not support my sound card so i need new drivers to install for the souncard.
I have read lots of forums where people had the same problem with the same sound cards, solution is to update alsa drivers to new ones.
I need at least alsa version 1.1.10rc2 
and in default packages there is only: 1.0.9b-4

but why the version file is missing, maybe the path is wrong in  alsa package?
don't know what to think :(

Fallen

---

### Post by mo_x on 2005-12-17
Install the correct version of the linux headers.
```
sudo apt-get install linux-headers-`uname -r`
```
Then point to the linux headers directory
```
--with-kernel /usr/src/linux-headers-<your kernel version>
```

---

### Post by fallen on 2005-12-17
Thanks that worked!
thanks 

but now there is another problem.
It tells that:
[PHP]*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.[/PHP]
how do I know what compiler was used and how do i use the one that was used?

and another thing:
[PHP]configure: error: You have built-in ALSA in your kernel.[/PHP]

so is there any way of upgrading an existing ALSA or what else I can do?
remove the old and configure with new, or just upgrade?
I'm new to the kernel things so can anyone help?
any ideas?

Fallen

---

### Post by mo_x on 2005-12-17
The Ubuntu kernel is compiled with gcc-3.4. You have to install it first. Then before running the configure script do:
```
export CC=/usr/bin/gcc-3.4
```

---

