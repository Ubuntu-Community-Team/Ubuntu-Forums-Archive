---
title: "Problem about vmware"
date: 2009-02-28
forum: General Help
---

### Post by peterjst on 2009-02-28
I install my ubuntu in the vmware
When I trying to install the vmware tools,
I got this message:

Your kernel was built with "gcc" version "4.2.3", while you are trying to use "/usr/bin/gcc" version "4.2.4". This configuration is not recommended and VMware Tools may crash if you'll continue. Please try to use exactly same compiler as one used for building your kernel. Do you want to go with compiler "/usr/bin/gcc" version "4.2.4" anyway? 

It seems that it fail to match the gcc version and the kernel version,
however, I don't know which version of gcc or kernel should I update.
Can anyone help me?

---

### Post by Xiong Chiamiov on 2009-02-28
You don't need to update anything, as you're using a version of gcc that's **newer** than the one the kernel was built with, unless your kernel's out of date.  In my experience, though, a minor point version off is nothing to worry about.

You may want to look into VirtualBox, too.  I find it a lot easier to use than VMware.

---

