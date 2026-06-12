---
title: "Disable Portmap Ubuntu 10.04"
date: 2011-02-03
forum: Desktop Environments
---

### Post by metallica1973 on 2011-02-03
I have attempted to disable portmap from loading up by deleting the symbolic links in:

[PHP]/etc/rc*.d  [/PHP]

but whenever I reboot the distro I run a netstat -pantu and I can see that portmap still loads. When I try doing a

[PHP]sudo update-rc.d portmap disable [/PHP]

, it cries and says:

[PHP]update-rc.d: warning: /etc/init.d/portmap missing LSB information 
update-rc.d: see<http:wiki.debian.org/LSBInitScripts> 
System start/stop links for /etc/init.d/portmap do not exist [/PHP]

---

