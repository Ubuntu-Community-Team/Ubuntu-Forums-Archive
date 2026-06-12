---
title: "synaptic package manager not opening"
date: 2009-03-15
forum: General Help
---

### Post by indstatinst on 2009-03-15
I am using Ubuntu Hardy. I am not able to install anything new. When I tried opening synaptic package manager, it displays massage with title 'An Error Occurred', saying 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.'.

I tried running the command 'dpkg --configure -a' on the terminal, but that gives an error message  'dpkg: requested operation requires superuser privilege'

Please help.

---

### Post by Elfy on 2009-03-15
Give it the rights by using sudo

```
sudo dpkg --configure -a
```

---

### Post by indstatinst on 2009-03-15
gr8 ! it works... i installed the updates

---

### Post by Johnr123 on 2009-04-08
Hey thanks also. Being new to Linux, I wasn't aware of the 'sudo ' command to gain superuser privilage. I had the same error message.

My issue began when using the "add/remove.." application to install "Wine." After the error emssage, I tried the synaptic package manager, but it gave the same error notification and wouldn't even start to allow me to selct an application. When I ran the 'sudo dpkg --configure -a' command, the issue was corrected.

Perhaps the problem occurred in my case by using "add/remove..." to install "Wine," rather than synaptic manager, since Wine requires upgrades to some current applications and the install of other related applications to be complete. I found that out when finally installing Wine through the Synaptic manager. When I tried to install through Add/Remove... it didn't mark any of the periferal upgrades and installs to be applied. Could that have caused the error?

---

### Post by Fourgun on 2009-04-11
YES!!! Thanks forestpixie I can now run synaptic package manager

---

