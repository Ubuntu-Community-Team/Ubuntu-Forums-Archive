---
title: "Kernel headers repo problem"
date: 2006-06-02
forum: Desktop Environments
---

### Post by nbx909 on 2006-06-02
Only the Linux 2.4.27 kernel headers are in the repos while 2.6.15-23 is what dapper ships with. I need the headers to compile vmware server. ](*,) So did somebody screw up at the repos or what? :confused:

---

### Post by nbx909 on 2006-06-02
I figured this was something that the developers forgot to put in the repos so i filed a bug [https://launchpad.net/distros/ubuntu/+source/linux-kernel-headers/+bug/48150](https://launchpad.net/distros/ubuntu/+source/linux-kernel-headers/+bug/48150)

---

### Post by jmacmich on 2006-06-03
I tripped on the same issue... they named the 2.6 kernel package 'linux' rather than 'kernel'... 
Do a search for 'linux-header' on packages.ubuntu.com

```
Package linux-headers-2.6.15-23

    * dapper (devel): Header files related to Linux kernel version 2.6.15
      2.6.15-23.39: amd64 i386 powerpc

Package linux-headers-2.6.15-23-386

    * dapper (devel): Linux kernel headers 2.6.15 on 386
      2.6.15-23.39: i386

Package linux-headers-2.6.15-23-686

    * dapper (devel): Linux kernel headers 2.6.15 on PPro/Celeron/PII/PIII/PIV SMP/UP
      2.6.15-23.39: i386

etc.
```

See also [this thread]("http://www.ubuntuforums.org/showthread.php?t=183209")

---

### Post by az on 2006-06-03
If you have installed from the live cd, you can boot inot your new system and while at the desktop, pop in the live cd again.  there is a small repo with essentil packages for building extra kernel modules and other networking things.  linux-headers-386 is on the repo.

Once you pop in the cd, you will be asked if you want to add those packages to your list of repos.

If you installed from the alternate cd, the linux-headers as well as all the other packages are already part of your source.list.

---

### Post by tiddlygoose on 2006-06-09
OK, so being new to this Ubuntu but not to VMWare Workstation... Where do I find the C Header files that match my running kernel once I have installed the linux-headers-2.6.15-23-686? Man do I have a lot to learn.

---

### Post by mcduck on 2006-06-09
[QUOTE=tiddlygoose]OK, so being new to this Ubuntu but not to VMWare Workstation... Where do I find the C Header files that match my running kernel once I have installed the linux-headers-2.6.15-23-686? Man do I have a lot to learn.[/QUOTE]
You should install linux-386, linux-686 or linux-K7 metapackage, depending on your CPU. That way you'll get the kernel, headers and restricted modules, and they'll always update to the latest available version.

So, in your case, 'sudo apt-get install linux-686' should get you everything you need :)

---

### Post by patrickfromspain on 2006-06-09
If you do a search for linux-headers in synaptic you'll get what you want ;)

---

### Post by gatorbrit on 2006-06-16
I am having a similar problem with the headers not matching...

First I do this...
```

richard@ubuntu:~$ uname -r
2.6.15-23-386

```

Then...
```

richard@ubuntu:~$ sudo apt-get install linux-headers-2.6.15-23-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.15-23-386

```


I also tried
```

richard@ubuntu:~$ sudo apt-get install linux-headers-`uname -r` build-essential xinetd
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-2.6.15-23-386

```


 I am trying to install "parallels" and it requires the headers - any suggestions.

---

### Post by gatorbrit on 2006-06-16
duhhhhh
I figured it out - needed to update the package info in synaptic first.

Then it went fine

---

