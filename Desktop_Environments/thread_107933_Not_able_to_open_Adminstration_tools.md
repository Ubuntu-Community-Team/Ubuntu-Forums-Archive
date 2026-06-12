---
title: "Not able to open Adminstration tools"
date: 2005-12-24
forum: Desktop Environments
---

### Post by heart_reaver on 2005-12-24
Hi there i have been installing some things and every thing was going ok. When i rebooted and try to open synaptic 

This is what i am getting after entering my password
===================================

Failed to run /usr/sbin/synaptic as user root:
 Child terminated with 1 status

====================================

---

### Post by cwaldbieser on 2005-12-24
[QUOTE=heart_reaver]Hi there i have been installing some things and every thing was going ok. When i rebooted and try to open synaptic 

This is what i am getting after entering my password
===================================

Failed to run /usr/sbin/synaptic as user root:
 Child terminated with 1 status

====================================[/QUOTE]
Maybe you could reconfigure synaptic with:
```

$ sudo dpkg-reconfigure synaptic

```

Can you still use apt-get?

---

