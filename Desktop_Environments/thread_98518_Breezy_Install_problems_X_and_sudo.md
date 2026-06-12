---
title: "Breezy Install problems: X and sudo"
date: 2005-12-03
forum: Desktop Environments
---

### Post by bonius on 2005-12-03
Hello.
I am trying to get Breezy to install on a machine with an Nvidia NFORCE 410 chipset.  The text-mode install works just fine until it tries to load X at the very end of phase 2.  Then X fails to load.  I suspect it's a problem with the on board video.  

So, I got the Nvidia binary drivers, but I can't get them to install because su doesn't seem to be working.  Does the installer add the user to the sudoers file later on in the install process?  

Any ideas?
Thanks,
Bonius

---

### Post by invalid on 2005-12-03
Su does not work, by default. This is because the root account is disabled by default, so su has nothing to go into. Sudo is what ubuntu uses. If you check the link in my signature, you will understand all the details of it.

To run a program as a superuser, try```
sudo whatever
```

Hope this helps,

Cheers,
Cb

---

