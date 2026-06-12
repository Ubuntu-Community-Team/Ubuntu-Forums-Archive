---
title: "Each kernel updates spam more boot options into grub"
date: 2009-01-19
forum: General Help
---

### Post by crazyfuturamanoob on 2009-01-19
Everytime I got a kernel-update, I get two more boot options into grub, which are something like this:
> 
ubuntu 8.10 xx.x-xx.xxx-xx
[recovery mode] ubuntu 8.10 xx.xxx.xxxx-xx

Those xxx.xxx-xxx things are the kernel version. Now I got about 20 boot options there. :(

I want the old kernel boot options to be removed/replaced by the new options when I get kernel updates.

And I want to get rid of the 20 old lines as well (except memtestX86 and windows).


This is the only thing in Ubuntu which pisses me off.

---

### Post by estyles on 2009-01-19
so edit your menu.lst file ```
gksu gedit /boot/grub/menu.lst
```

You can safely delete entries for older kernel versions, and there are also comments in there that tell you how to set up the "Automagic Kernels" entries, or whatever it's called, that will limit the number of older kernel versions that are added.

---

### Post by meindian523 on 2009-01-19
Put howmany=1,so that > ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=allis changed to > ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
#howmany=1

---

### Post by meindian523 on 2009-01-19
And you can save some disk space by removing all but the most recent working kernel with ```
sudo apt-get remove linux-image-2.6.xx-x-generic
```
A side effect of this is that the entries are automatically removed from the menu.lst and thus from the Grub menu.

---

### Post by estyles on 2009-01-19
> **meindian523 said:**
> is changed to
Quote:
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
howmany=1 

I'm pretty sure you need to leave the "howmany=1" line commented out, so it should be #howmany=1.  You can try it both ways, but I think the instructions for automagic kernel entries say to leave the options commented out, because they aren't read by grub, they're just read when menu.lst is updated, and the updater knows to read the commented out lines as long as they have a single "#" and not "##".

---

### Post by meindian523 on 2009-01-19
Argh,the thanks feature is not yet back.Thank you estyles.And OP,follow estyles,there is no need to remove the preceding hash.I've corrected my post accordingly.

---

