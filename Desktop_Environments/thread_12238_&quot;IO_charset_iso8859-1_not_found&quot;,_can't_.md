---
title: "&quot;IO charset iso8859-1 not found&quot;, can't mount my windows partition"
date: 2005-01-23
forum: Desktop Environments
---

### Post by tjfitz on 2005-01-23
When trying to mount my windows partition, I keep getting the error:
> mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When I do "dmesg | tail" I get:
> ......
Unable to load NLS charset iso8859-1
FAT: IO charset iso8859-1 not found

I wasn't having this problem before compiling a nice nitro-sources kernel (2.6.10).  After getting this error the first time, I looked through my kernel configuration, and I had compiled support for iso8859-1 into the kernel (not as a module).  I compiled it again clean but I'm still getting the error.  All I could find when I googled was:
> 
The National Language Support in the kernel is not satisfied with the
 modules you are trying to load. The FAT file systems now have an option
 with which you can set the codepage. I have in /etc/fstab the following:
 
 /dev/hda1               /dos/c          vfat  umask=002,gid=35,codepage=850
 
 This loads the 850 codepage used here in germany......

I, however, am NOT in Germany, and I have no idea what codepage I would need.  How do I get this charset to load, or as an alternate, what options would I need to use to mount this filesystem (it's vfat)?

Thanks!

---

### Post by tjfitz on 2005-01-23
Ok, on a hunch, I tried recompiling the kernel again, only with iso8859-1 as a module instead of compiled directly into the kernel, and it works!  Strange, though, my roommate's kernel has it compiled directly in and his works fine....

---

