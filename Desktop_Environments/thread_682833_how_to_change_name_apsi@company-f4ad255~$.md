---
title: "how to change name?: apsi@company-f4ad255:~$"
date: 2008-01-30
forum: Desktop Environments
---

### Post by Underpants on 2008-01-30
how do I change the locally echoed hostname? 

apsi@company-f4ad255:~$

I think it's getting that name from a stale reverse dns entry or something. I want to statically assign it from within the system?

---

### Post by Giannis68 on 2008-01-30
System -> Administration -> Networking
General Tab -> Host Settings -> Hostname

reboot

---

### Post by Underpants on 2008-01-30
Forgot to mention, that I'm command line only. No GUI.

---

### Post by mali2297 on 2008-01-30
> 
**Permanent hostname change on Debian based Linux systems**

Debian based systems use the file /etc/hostname to read the hostname of the system at boot time and set it up using the init script /etc/init.d/hostname.sh

#cat /etc/hostname

debianadmin

So on a Debian based system we can edit the file /etc/hostname and change the name of the system and then run

/etc/init.d/hostname.sh startto make the change active. The hostname saved in this file (/etc/hostname) will be preserved on system reboot (and will be set using the same script we used hostname.sh).


From this [source]("http://www.debianadmin.com/change-hostname-or-server-name-of-a-linux-machine.html").

---

