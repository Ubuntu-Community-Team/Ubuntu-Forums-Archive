---
title: "grub won't hide or timeout"
date: 2011-06-10
forum: Desktop Environments
---

### Post by vancouverite on 2011-06-10
Hello,
I have just installed 11.04 on an Acer Aspire 3810TZ and the problem I'm having is that GRUB always shows, even though ubuntu is the only OS on the machine.

This wouldn't be a problem, except that there is no timer running, so if I forget to select the OS, then it will just sit there waiting - forever.

I have tried setting GRUB_HIDDEN_TIMEOUT=0 by:
 editing /etc/default/grub (then $sudo update-grub)
 configuring with startup-manager
 configuring with grub-customizer

and none of them work.  I have also tried setting a timeout of 3 seconds (as that would be better than infinite) and it doesn't work.

Any recommendations?

Van
Ubuntu Natty 32bit, fresh install
grub-common 1.99~rc1-13ubuntu3
grub-pc 1.99~rc1-13ubuntu3

---

