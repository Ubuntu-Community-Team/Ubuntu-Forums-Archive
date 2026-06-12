---
title: "nvidia and the 2.6.12.10 kernel files"
date: 2005-11-26
forum: Desktop Environments
---

### Post by shan2on_power on 2005-11-26
hi all, 
I was just wondering where to find the linux-header files and the linux-source files for the newest 2.6.12.10 kernel for the newest ubuntu release.  

I am a long time user of debian, and have just recently converted over to allow my pentium4 box to become the ultimate windows replacement.

The problems i have are when installing the nvidia driver occur [using the method of the original poster], after i change my xorg.conf file to use the **nvidia** driver rather than the freeware version of the **nv** driver.  gdm attempts to restart and then crashes. I am on my another box, so a detailed copy of the error message is unavailable.

When browsing synaptic, I find the latest to be 2.6.10.x [something]... 

**Question #1::**

Do i add another source to the sources.list file to get the newest header and source files??

or

**Question #2::**

Can i use on of the older header files just to compile the nvidia kernel locally?


Im not that much of a linux n00b [i've used slackware since 7.3], so a detailed explanation of what to do would help if any available.

thanks in advance

~shan2on

---

### Post by metoo on 2005-11-27
I would not compile nvidia modules myself at all.
They are in the linux-restricted-modules-yourkernel package. Already compiled and ready to use.

Search in synaptic for the other nvidia packages (GLX etc.). It's all there.

I'm missing the repository, but if they don't show up for you, add ' restricted  universe multiverse' to your sources.list . (well these are probably in restricted... :-) )

The kernel source package is 'linux-source-2.6.12' (synaptic tells you the actual version -10.24 on amd64 right now).

If you don't have X (temporary via nv?) then use
sudo apt-cache search name
to get a list of packages and use
apt-get install name
to install the package.

---

