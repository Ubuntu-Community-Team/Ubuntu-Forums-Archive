---
title: "how can I change/view the order daemons are started?"
date: 2006-01-28
forum: Desktop Environments
---

### Post by tariqf on 2006-01-28
I have a problem in that I get my NFS will not start up on boot - this has happened every sine I upgraded from hoary to breezy. I get 

   Starting rpc mountd ... [FAIL]

But if I manually restart nfs-common first then nfs-kernel-server everything starts and works fine. 

Please can someone tell me how I check and make sure that nfs-common gets started before nfs-kernel-server?

---

### Post by amohanty on 2006-01-28
The startup scripts are in /etc/rcS.d and /etc/rc2.d. Those are the only ones you need to care about. These folders contain links to files in /etc/init.d/

The files in rcS.d are executed everytime at startup and the ones in rc2.d are executed whenever the system enters runlevel 2 (the gui mode in ubuntu). To get more details google for 'runlevels introduction'.

Now in these folders you will see symbolic links starting with an SXXyyyy or a KXXyyyy where XX is a number and yyyy is the name of the original script in /etc/init.d The scripts starting with an S are executed at startup and those starting with a K are executed at shutdown. The numbers XX indicate the order in which they are executed so S10scriptA is executed before S12scriptB.

So check the links to nfs-common and nfs-kernel-server and make sure the numbering is correct. Although I suspect your problem may have another source because the nfs installer should have created the right links.

HTH
AM

---

