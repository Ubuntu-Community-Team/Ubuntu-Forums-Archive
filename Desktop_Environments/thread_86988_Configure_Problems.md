---
title: "Configure Problems"
date: 2005-11-07
forum: Desktop Environments
---

### Post by bwainscott on 2005-11-07
I have had nothing but trouble on the compiling side of the house.  terminal gives the following when trying to run configure:

checking size of long... 4
checking size of char *... 4
checking size of char... 1
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for extra includes... no
checking for extra libs... no
checking for libz... configure: error: not found. Check your installation and look into config.log


Please let me know how to fix this so I can continue.

Thanks
Bob

---

### Post by bwainscott on 2005-11-07
says some stuff in config.log about confdefs.h failing

---

### Post by RAOF on 2005-11-07
Firstly, what are you trying to install?  Building from source should be your last resort.  Look here for the ["how to install stuff"]("http://help.ubuntu.com/starterguide/C/ch02.html") guide.

You'll need to look at that, even if you still want to compile from source.  Because you'll need to install the "zlib1g-dev" package.

---

