---
title: "Breezy + Adaptec i2o RAID = Workaround"
date: 2005-10-18
forum: Desktop Environments
---

### Post by WorLord on 2005-10-18
Hello, 

This is a workaround to allow Breezy's default kernel to boot on the Adaptec Raids that use the dpt_i2o drivers (and currently cause kernel panics on Breezy).

I don't know what good it is, because without a working kernel, I don't see how this workaround could be applied... but perhaps one can boot into single-user mode or something to do it.  I upgraded from Hoary, and had the luxury of being able to boot Breezy using Hoary's kernel to do this – perhaps it is useful to people in that particular camp.  

Note: Wherever "[kernel version]" is listed, use the name of the kernel you are trying to fix – typically, this will be “2.6.12-9-386”.  

First, you'll want to delete the newer i2o driver, as this is the one messing things up (I've tried booting with only this driver, and it still doesn't work).  In a console, type:

```
sudo rm -rf /lib/modules/[kernel version]/kernel/drivers/message/i2o/
```

Now that these modules are gone from the kernel's module tree, you'll want to re-run depmod (so the kernel doesn't look for modules that are no longer there):

```
sudo depmod [kernel version]
```

Next, you'll want to re-build the initrd and some other various and sundry things.  This is most simply accomplished by reconfiguring the kernel using DPKG: 

```
sudo dpkg-reconfigure linux-image-[kernel version]
```

Et voila.  You should be able to boot Breezy with Breezy's own kernel, with all the customizations and niceties (like Usplash!).  

I hope this is helpful.  I also hope the Kernel gets patched soon, and the ISO's get updated to reflect a working Breezy kernel for i2o devices.

---

### Post by matthurne on 2005-10-24
Most certainly helpful.  Too bad there's no way to work around it in the installer itself - I can't say I feel as confident about a server running Hoary upgraded to Breezy and then somewhat hacked to boot.

*sigh*

But its better than nothing, thanks for the How-To.  :)

---

### Post by Z3K3 on 2005-11-06
worked for me too.  hopefully this will be resolved in future installcd's.  I'd hope they drop the i2o and only load it if manually selected or configured by the administrator.

---

