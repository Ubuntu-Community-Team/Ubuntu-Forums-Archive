---
title: "default run levels?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by honeydew on 2006-06-04
what is the run level for multiuser, no desktop(server mode).  Im used to it being run level 3 on many linux systems. I checked inittab and it was set to a default of 2, this is def not what I was expecting ](*,)   any advice and achieving what I want would be most pleasent.

thanks!

---

### Post by nanotube on 2006-06-04
in ubuntu all runlevels 2-5 are the same. 
default runlevel is 2
if you want to make runlevel 3 (for example) to not start the X system, just edit your /etc/rc3.d/ and remove the link to gdm (or kdm, if you use kde).
a good way to edit runlevel config is to install package "sysv-rc-conf", it will help you out. then you can use it and just uncheck gdm from runlevel 3.

---

