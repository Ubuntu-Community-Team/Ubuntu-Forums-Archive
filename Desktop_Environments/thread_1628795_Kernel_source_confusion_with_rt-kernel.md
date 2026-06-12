---
title: "Kernel source confusion with rt-kernel"
date: 2010-11-23
forum: Desktop Environments
---

### Post by maddis on 2010-11-23
I'm not sure if this is entirely correct place, but there wasn't any programming related subforums so here goes.

I've been working with the rt-kernel and for now the precompiled version has been sufficient. For some reason, the rt-kernel has been always older than the generic so now it lacks the support for cirrus hda-driver that the current generic kernel has. Support was easily ported from generic to rt and then I just recompiled the kernel. 

So far so good.

Then I started installing psb display drivers and they are compiled against the kernel headers and then I made a discovery that the rt-kernel sources don't actually match the precompiled image.

I've taken the kernel sources out with command: 
```
apt-get source linux-image-2.6.31-11-rt
```
I've compiled it with commands:
```
fakeroot debian/rules clean
AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-rt
```

I also tried target binary-debs, but it made no difference.

There are at least anon_up_write and _atomic_spin_lock - functions missing among others that are not listed here. They can be found from a patch kernel-src-dir/debian/patches/patch-2.6.31.12-rt21. Some reason that patch gets never added to actual kernel source tree. I tried to apply it by hand, but the results wasn't very good. Most of the files that should've been patched failed.

Is this a bug or am I doing something wrong?

---

### Post by maddis on 2010-11-24
For some reason those patches are not applied to kernel when compiling. When applied by hand everything seems to be just fine. 

They can be applied with command;
```
QUILT_PATCHES=debian/patches quilt push -a
```

---

