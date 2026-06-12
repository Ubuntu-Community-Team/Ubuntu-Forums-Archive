---
title: "Help with Parallels (config fails)"
date: 2006-10-19
forum: Desktop Environments
---

### Post by crthomas on 2006-10-19
I am trying to install parallels.  I have installed all of the packages listed in the documentation, but when I run parallels-config, it fails.

 sudo parallels-config 


     Compiling Parallels Workstation 2.2 drivers...
     Drivers have been compiled successfully.
     Installing drivers...
     Starting drivers...
Loading Parallels Workstation 2.2 hypervisor ... 
FATAL: Error inserting hypervisor (/lib/modules/2.6.15-26-386/kernel/drivers/misc/parallels/hypervisor.ko): Operation not permitted
 Can not load hypervisor module.
Parallels Workstation drivers were successfully configured
and compiled but cannot be started (insmod command failed).
Run 'dmesg' command for more information.

---

### Post by pete on 2006-10-21
Don't know if it will help, but there's a thread in the Parallels forums from a couple people having exactly the same problem in RH and FC:

[http://forums.parallels.com/showthread.php?t=2874&highlight=Error+inserting+hypervisor]("http://forums.parallels.com/showthread.php?t=2874&highlight=Error+inserting+hypervisor")

If I read the fix correctly, it looks like the workaround from the Parallels team is to completely remove the hypervisor install and re-run the workstation install/config.

---

