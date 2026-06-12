---
title: "We need a new kernel specific forum section"
date: 2006-10-07
forum: Desktop Environments
---

### Post by harisund on 2006-10-07
Hello

I understand Ubuntu is meant for newbs and all that... but still, Are there advanced users who are using Ubuntu, or is that a myth:Advanced users using Ubuntu? Where do I go for kernel specific questions? 

I spent many hours asking repeatedly questions in the IRC, and apparently nobody has compiled their own kernel there. 

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild) <-- This page is the closest I could find. In it there's a line that looks like:

> The stock Ubuntu configs are located in debian/config/ARCH/ where ARCH is the architecture you are building for. In this directory are several files. The config file is the base for all targets in that architecture

However there is absolutely no such folder in my machine, even after installing the source package. (And the wiki page talks about a mysterious package called linux-source-2.6.17 which doesn't exist in the repos, atleast not the default ones.)

Where do I go? What do I do?

---

### Post by harisund on 2006-10-07
Hello

I understand Ubuntu is meant for newbs and all that... but still, Are there advanced users who are using Ubuntu, or is that a myth:Advanced users using Ubuntu? Where do I go for kernel specific questions? 

I spent many hours asking repeatedly questions in the IRC, and apparently nobody has compiled their own kernel there. 

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild) <-- This page is the closest I could find. In it there's a line that looks like:

> The stock Ubuntu configs are located in debian/config/ARCH/ where ARCH is the architecture you are building for. In this directory are several files. The config file is the base for all targets in that architecture

However there is absolutely no such folder in my machine, even after installing the source package. (And the wiki page talks about a mysterious package called linux-source-2.6.17 which doesn't exist in the repos, atleast not the default ones.)

Where do I go? What do I do?

EDIT: Why did this appear twice?

---

### Post by po0f on 2006-10-07
harisund,

I've installed the linux-headers package on my box, and it comes with a .config file:
```
$ locate .config
(snip)
/usr/src/linux-headers-2.6.17-10-generic/.config
(snip)
```

I believe this is the config for the kernel I am using.

If I were to compile my own kernel, I wouldn't even use the sources that are in the repositories.  Just go out and grab a vanilla kernel and patch away!

---

### Post by harisund on 2006-10-08
First, why doesn't the wiki page mention anything about linux-headers? 

And I want the kernel with the Ubuntu patches, and I don't know where to find the Ubuntu specific patches for the vanilla kernel. 

But what about the debian/config/x86/ folder that the wiki is talking about? Should somebody edit the wiki then?

---

### Post by po0f on 2006-10-08
harisund,

I believe [this](http://packages.ubuntu.com/dapper/devel/linux-source-2.6.15) is the package you want to install.  It will install a tarball in /usr/src, ie /usr/src/linux-source-2.6.15.tar.bz2, that you will have to manually unpack.  I don't know if the kernel is already patched with Ubuntu patches or not.  Only one way to find out.  :)

To get the kernel source, just apt-get install linux-source-2.6.15.  I glanced through the wiki page.  It's not the way I would build a new kernel, but the instructions seem fairly complete.

And about the package discrepancy on the wiki, disregard it.  It looks like someone half-way editted it to reflect Edgy's new kernel, which is 2.6.17.  There are still references to 2.6.15 though.  This is the main reason I avoid wikis.  ;)

---

### Post by harisund on 2006-10-08
Good point po0f. I will follow your advice. Thanks a ton! :)

---

