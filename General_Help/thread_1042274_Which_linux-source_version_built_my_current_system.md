---
title: "Which linux-source version built my current system?"
date: 2009-01-17
forum: General Help
---

### Post by Gustra on 2009-01-17
I'm running Kubuntu 8.10, but I think this question is valid for all versions.

How do I determine which kernel source was used to build my current version?

"rname -r" returns "2.6.27-9-generic", but there is no such corresponding linux-source package (i.e. linux-source-2.6.27-9-generic does not exist in the package list).

"/lib/modules/`uname -r`/build" points to the current header files, but I cannot find any corresponding link or datum for the source.

The only available linux-source package is 2.6.27 which installs /usr/src/linux-source-2.6.27 (untared), but how do I know whether that is the correct source package? Somehow I don't think `uname -r | sed -e 's/\-.*//'` is the correct way to do it... :-k

---

### Post by sdennie on 2009-01-17
You could try:

```

sudo apt-get source linux-image-`uname -r`

```

But, that might be complicated to build.  If you have the linux-source tarball sitting in /usr/src, it's probably very, very similar to the -generic kernel (if not identical).  The difference between, for instance, the -generic and -server kernels is mostly in the config used to build the kernel.  The config used can be found with:

```

cat /boot/config-`uname -r`

```

---

### Post by Gustra on 2009-01-18
Yep, that worked to get the source! I had missed the "source" command to apt-get.

And from what I see, it appears that it is indeed possible to use the uname+sed trick above to determine the kernel version used to build the system! The rest is Ubuntu patches (-9-19 for 2.6.27-9-generic).

Many thanks!

---

