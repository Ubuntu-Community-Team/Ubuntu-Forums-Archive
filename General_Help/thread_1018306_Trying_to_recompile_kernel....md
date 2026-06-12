---
title: "Trying to recompile kernel..."
date: 2008-12-22
forum: General Help
---

### Post by Crafty Kisses on 2008-12-22
Hey folks, I'm running Ubuntu 8.04, recently I'm having major sound issues, I'm pretty familiar with the Linux kernel and I'm trying to recompile it, but the main issue it's not giving me a kernel to select, this is very odd. So for example, I run the following commands:
```
make dep
make bzImage
make modules
make modules_install
```
Then reboot, then I don't see a kernel anywhere I can select from, I also tried copying the /boot file by running the following:
```
cp /codename/src/arch/x64/boot/bzImage /boot/newkernel
```
I also edited the following config file to the following:
```
image = /boot/newkernel
label = new
read-only
```
I still get no kernel selection at the main screen. I also run the following: ```
uname -a
``` It does actually say I'm using the "**2.6.22-14-generic**" kernel. I also have another issue, I've searched this on the forums and Google, still nothing. Supposedly it thinks I compiled this kernel with: 
```
CONFIG_INPUT_UINPUT
``` I'm trying to compile the 2.6.25 kernel. I also ran the following: ```
cat /boot/config-2.6.22-14-generic | grep UINPUT
```Just to see if that option even exists with the current config file I'm using, and there doesn't appear to be an option. It just doesn't make sense, I have vast Linux knowledge, so any suggestions, I'm really stumped on this one.

---

### Post by igknighted on 2008-12-22
Try using this guide for recompiling your kernel [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158).  This is how I always do it, and it has always worked great for me.

Kernel 2.6.22? Why such an old version?

---

