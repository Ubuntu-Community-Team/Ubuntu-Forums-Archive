---
title: "Desktop corrupted - Multiple duplicate desktops"
date: 2014-06-08
forum: Desktop Environments
---

### Post by engeeaitch on 2014-06-08
I'm running Ubuntu 12.04 in a VM (VMware Player 6.0.2)

After some recent updates, my desktop has suddenly become corrupt - it has become duplicated three times - I've attached a screen shot. Each 'desktop' seems to be replicated - changing one 'desktop' results in the other 'desktop' changing.

I've tried a few things along the lines of reset and re-install, but I don't really know where to go from here.

Any help much appreciated.

Edit:  I've just noticed that I have exactly the same problem as here: [http://ubuntuforums.org/showthread.php?t=2228472](http://ubuntuforums.org/showthread.php?t=2228472) 
The solution would appear to be to force the use of the vmware graphics driver, rather than the driver supplied by ubuntu, but I don't know how to do this (I've tried vmware-config-tools.pl --overwrite but this did not make any difference.

---

### Post by Dominicus on 2014-06-11
A workaround is to revert the kernel back to v3.2.0.63 as discussed in this VMware forum post:
[https://communities.vmware.com/message/2389802#2389802](https://communities.vmware.com/message/2389802#2389802)

...and hope for a future kernel and/or vmware X driver that work together.

---

### Post by Dominicus on 2014-06-28
Issue is now reported for kernels 3.2.0.64 and 3.2.0.65.

How does this get picked up or acknowledged?  Workaround involve reverting back to last-working version of kernel (3.2.0.63).
Issue seems to be incompatibility between newer kernels, and the vmWare video driver packaged with Ubuntu 12.04 LTS (dated 2012).

[https://communities.vmware.com/message/2396263#2396263](https://communities.vmware.com/message/2396263#2396263)

---

