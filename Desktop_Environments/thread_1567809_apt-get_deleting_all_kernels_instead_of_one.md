---
title: "apt-get deleting all kernels instead of one"
date: 2010-09-04
forum: Desktop Environments
---

### Post by oh my on 2010-09-04
Hi,

I have an issue with apt-get that has been bugging me, namely that it tries to delete kernels I did not specify for deletion.

This is an issue that has been present over at least the last three releases and is present for both 32bit and 64bit, so it might actually be a feature and not a bug, however I can't see it's usefulness.

When I use the command:
```
sudo apt-get remove --purge 2.6.32-21*
```It not only tries to remove the kernel **2.6.32.21** but gives me the following output:

```
 sudo apt-get remove --purge 2.6.32-22*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting linux-headers-lbm-2.6.32-24-generic for regex '2.6.32-22*'
Note, selecting linux-headers-2.6.32-21-preempt for regex '2.6.32-22*'
Note, selecting linux-backports-modules-alsa-2.6.32-21-generic for regex '2.6.32-22*'
Note, selecting linux-backports-modules-wireless-2.6.32-22-server for regex '2.6.32-22*'
[....] 
shortened
[....]
Note, selecting linux-image-2.6.32-24-generic-pae for regex '2.6.32-22*'
Note, selecting linux-headers-2.6.32-23-generic for regex '2.6.32-22*'
The following packages will be REMOVED:
  linux-generic* linux-headers-2.6.32-22* linux-headers-2.6.32-22-generic* linux-headers-2.6.32-23*
  linux-headers-2.6.32-23-generic* linux-headers-2.6.32-24* linux-headers-2.6.32-24-generic*
  linux-headers-generic* linux-image-2.6.32-22-generic* linux-image-2.6.32-23-generic*
  linux-image-2.6.32-24-generic* linux-image-generic*
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
After this operation, 637MB disk space will be freed.
Do you want to continue [Y/n]? 

```I shortened the log. Full log here: [http://pastebin.com/jCBExTka](http://pastebin.com/jCBExTka)
Meaning it is happily trying to delete the specified kernel **2.6.32.22**, but also the kernels **2.6.32.23**,** 2.6.32.21** and my current and latest kernel **2.6.32.24**.

When I go through with this command to remove the oldest kernel on the system, it will actually delete all kernels present on my PC (as I painfully learned when I first tried it). Why is that the case? Wouldn't it make more sense to only remove the kernel **2.6.32.22**?

regards oh my

---

### Post by 3Miro on 2010-09-04
One of two things are happening:

1: 2.6.32-22* looks not only for package names, but also for package descriptions (or is buggy) and thus it selects more packages then it should. Try specifying
```
 sudo apt-get remove --purge linux-headers-2.6.32-22-generic 
```
also
```
 sudo apt-get remove --purge linux-image-2.6.32-22-generic 
```
and see if this is selecting more packages than it should.

2: If we still have more packages selected than necessary, then there is something going on with the dependencies. Try looking into aptitude or a graphical package manager to see what exactly the dependencies are.

---

### Post by oh my on 2010-09-04
Hi 3miro,

I know how to uninstall a kernel. My point is more that the fact that apt will happily delete kernels that **do not match** the specified criteria for uninstalling is dangerous. Who would expect it?

For a matter of fact the command [b]sudo apt-get remove --purge 2.6.32-22-*
[/b] will do exactly what you would expect, namely uninstall all packages belonging to the 2.6.32-22 kernel.  See here:
```
sudo apt-get remove --purge 2.6.32-22-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting linux-backports-modules-wireless-2.6.32-22-server for regex '2.6.32-22-*'
Note, selecting linux-headers-lbm-2.6.32-22-preempt for regex '2.6.32-22-*'
Note, selecting linux-backports-modules-wireless-2.6.32-22-preempt for regex '2.6.32-22-*'
Note, selecting linux-backports-modules-alsa-2.6.32-22-preempt for regex '2.6.32-22-*'
Note, selecting linux-image-2.6.32-22-preempt for regex '2.6.32-22-*'
Note, selecting linux-tools-2.6.32-22 for regex '2.6.32-22-*'
Note, selecting linux-headers-lbm-2.6.32-22-generic for regex '2.6.32-22-*'
Note, selecting linux-image-2.6.32-22-virtual for regex '2.6.32-22-*'
Note, selecting linux-backports-modules-wireless-2.6.32-22-generic for regex '2.6.32-22-*'
Note, selecting linux-image-2.6.32-22-generic-pae for regex '2.6.32-22-*'
Note, selecting linux-backports-modules-alsa-2.6.32-22-server for regex '2.6.32-22-*'
Note, selecting linux-headers-2.6.32-22-preempt for regex '2.6.32-22-*'
Note, selecting linux-backports-modules-alsa-2.6.32-22-generic for regex '2.6.32-22-*'
Note, selecting linux-image-2.6.32-22-generic for regex '2.6.32-22-*'
Note, selecting linux-headers-2.6.32-22 for regex '2.6.32-22-*'
Note, selecting linux-headers-lbm-2.6.32-22-server for regex '2.6.32-22-*'
Note, selecting linux-headers-2.6.32-22-generic for regex '2.6.32-22-*'
Note, selecting linux-image-2.6.32-22-server for regex '2.6.32-22-*'
Note, selecting linux-headers-2.6.32-22-server for regex '2.6.32-22-*'
The following packages will be REMOVED:
  linux-headers-2.6.32-22* linux-headers-2.6.32-22-generic* linux-image-2.6.32-22-generic*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 210MB disk space will be freed.
Do you want to continue [Y/n]? n 

```


I thought there might be a reason why the other one isn't matching... Maybe?

regards myrti

---

### Post by oh my on 2011-01-13
Turns out I just know squad about regular expressions. The command does what it is asked too, only that a n00b like me doesn't know what their aksing.

***** means "followed by 0 or more of the preceding caracter"

So when I asked to delete anything that matched "2.6.32-21*" I asked for anything that started with "2.6.32-2" followed by 0 or more 1s. 
Obviously 2.6.32.25 is "2.6.32-2" followed by no 1, so it will match the expression "2.6.32-21*"

Just thought I'd share.

---

### Post by Legeril on 2011-01-13
type this into the terminal, it will delete all unecessary kernels

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

Simple.

---

### Post by inobe on 2011-01-13
> **Legeril said:**
> type this into the terminal, it will delete all unecessary kernels

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

Simple.

i will verify that this command will clear out all "unused" kernel headers, kernel images and modules.


be sure to remove any hard drives with operating systems that are not part of your dual boot setup, for example, your trying to extract data from a customers windows drive!

after running the command grub updates, that drive will be added as a dual boot disc :P

---

### Post by oh my on 2011-01-13
I'm personally not a fan of that particular command, because I like to have at least one backup kernel in case the latest one isn't working for me.

If I were to run that command after a kernel upgrade to remove the "unused kernels" I might be left with no working kernel. For safety measures there should be one or two of the older kernels installed as well in case the latest kernel goes south for whatever reason.

---

