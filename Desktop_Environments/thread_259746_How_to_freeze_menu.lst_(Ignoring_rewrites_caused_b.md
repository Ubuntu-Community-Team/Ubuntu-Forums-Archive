---
title: "How to freeze menu.lst? (Ignoring rewrites caused by kernel updates)"
date: 2006-09-17
forum: Desktop Environments
---

### Post by cumic on 2006-09-17
First of all, hi ubuntu lovers!

I'm in an annoying situation, and I supposed most people is in the same situation. Ok, it's not very annoying, but I'm lazy enough to request some help...

I have a customized menu.lst, which allows me to boot, thanks to grub, in three OS (Ubuntu, Vista and MacOS X, but it doesn't matter for this question).

When there is a kernel update, the menu.lst regenerates itself, and adds a lot of stuff I don't want, differents versions of the kernels, mainly. Of course, I have the lines that belongs to the others OS out of the "dynamic section", and they are safe (but eclipsed by the Ubuntu lines).

Ok, my question is simple: How do I change this behavior in order to ignore the menu.lst's changes due to the successive kernel updates?

Better, could I maintain my customized menu.lst, but, simultaneously, change only the line updated Ubuntu kernel?

A lots of thanks, Ubuntu community is the best! (with an enormous difference)

---

### Post by escape on 2006-09-17
Just a guess, it may cause your computer to not boot up, but try chmodding menu.lst to 444 (default is currently 644).

---

