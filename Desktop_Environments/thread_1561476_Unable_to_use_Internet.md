---
title: "Unable to use Internet"
date: 2010-08-26
forum: Desktop Environments
---

### Post by Balajisadhu on 2010-08-26
Hi all,

I am Balaji, using ubuntu 9.04 in my desktop, i was using internet in that, but automatically it is not working now. So Please can anyone provide me help.

Regards,
Toruk Macto

---

### Post by grief -l on 2010-08-26
Did automatic update supply you with a new kernel? Just boot off the old one. Did some security update supply you with a new or patched driver? Blacklist it.

---

### Post by x1a4 on 2010-08-26
Is your network manager running?  If so, click it and select Connect option.  Sorry for not being more specific but I don't use the default network manager as I had the same problem as you.  Periodically my connection would drop and I had to reconnect.  I was able to fix it by replacing network manager with wicd--a better network manager.  

You can also try:
```
sudo ifdown eth0
sudo ifup eth0
```
This will take down your network interface then bring it back up. 

Where 'eth0' is the name of your network interface. If  you have only one and you haven't renamed it and it's an ethernet card it should be 'eth0'.

---

### Post by monk11 on 2010-10-12
Though the post is old, but some may find it useful. 
I am running 9.10 and took update and after restarting the system, wicd fails to connect to internet. The reason was quite weird as wired-settings.conf configuration file has some extra characters ('[]' with some junk lines) and it was giving parsing errors and failing the entire wicd process. Quite bizarre as it was updated automatically (I think via the updates). Removing them solved the problem.

---

