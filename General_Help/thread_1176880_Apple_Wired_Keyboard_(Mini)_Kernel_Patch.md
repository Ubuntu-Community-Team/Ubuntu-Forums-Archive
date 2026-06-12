---
title: "Apple Wired Keyboard (Mini) Kernel Patch"
date: 2009-06-02
forum: General Help
---

### Post by coffeeturtle on 2009-06-02
I found the following kernel bug that prevents the new aluminum apple mini wired keyboard from being recognized

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339382](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339382)


One of the posters shared a link to the patch

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=fef3f571ecc2a82395c531d97b3f71a59e04e946](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=fef3f571ecc2a82395c531d97b3f71a59e04e946)


I have two questions:

1.) Has this been merged into any of the repositories yet?

2.) I am familiar with applying patches using patch, but I have never patched kernel drivers before and I don't really want anything to go wrong.  Also I assume that since I would be patching a c file that like any other program it would need to be recompiled for the change to take effect.  I looked in the /usr/src directory though and there are no driver files, can someone explain why this is so?  I have read articles discussing how to recompile kernels but the instructions are not general and only describe how to upgrade the entire kernel which I will not be doing.  Can anyone provide specific steps that explain how to apply the patch successfully and what each step is doing?

Any help is much appreciated, thanks guys.

Some information about my machine:

$ uname -a
Linux user-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

nVidia 180.44 restricted video driver in use

---

### Post by coffeeturtle on 2009-06-03
bump for some help please

---

### Post by coffeeturtle on 2009-06-03
bumping once more

---

### Post by mr_skater99 on 2009-06-04
I'm thinking of getting one of these for work - i love my macbook keyboard.

Would love to know if this is going to make it up stream.

---

### Post by Mike'sHardLinux on 2009-06-04
My mistake. Wrong keyboard. Didnt realize there was another new one.

---

### Post by coffeeturtle on 2009-06-04
bumping again

i know i can do this, i just need a little bit of guidance from someone with experience so I don't damage my kernel

---

