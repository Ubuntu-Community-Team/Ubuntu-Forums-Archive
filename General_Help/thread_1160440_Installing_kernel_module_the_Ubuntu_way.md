---
title: "Installing kernel module the Ubuntu way"
date: 2009-05-15
forum: General Help
---

### Post by jadamcrain on 2009-05-15
I have kernel module I compiled from source code on 8.04 desktop. I'm under NDA from the manufacturer and I can't name the device, let's call the built file xyz.ko

The manufacturer suggests adding the  following to a boot up shell scripts such as /etc/rc.local

"insmod /YOURLOCATION/xyz.ko"

Is this really the right way to do this? I don't want to leave the module binary in a subdirectory of my home dir. Shouldn't it go somewhere special like a subdirectory of /lib/modules?

Any advice would be appreciated.

thanks, Adam

---

