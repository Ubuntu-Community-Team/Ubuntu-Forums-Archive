---
title: "Citrix XenApp client on Ubuntu 11.10"
date: 2012-04-22
forum: Desktop Environments
---

### Post by MooFx on 2012-04-22
Hi,

I am trying to get the Citrix XenApp client working on my Ubuntu 11.10 dekstop.
So far I've installed OpenJDK Java 7 Runtime and the Citrix XenApp receiver for Linux 11.100. 
After I logged on with the RSA SecurID token and try to start powerfuse I keep getting the following error.

[IMG]http://i.imgur.com/1DR1I.png[/IMG]

Does anyone know what to do?

Thanks in advance!

****Update:** After I installed [Linuxx86.tar.gz]("https://portal.parnassiabavogroep.nl/http/10.130.1.32/Citrix/AccessPlatform/Clients_common/en/icaunix/linuxx86.tar.gz") I got the following error:

[IMG]http://i.imgur.com/AguEs.png[/IMG]

---

### Post by Toz on 2012-04-22
I have a similar setup at work, and to make a long story short, does setting kernel.yama.ptrace_scope to 0 allow the connection?
```
sudo echo 0 > /proc/sys/kernel/yama/ptrace_scope
```

---

### Post by MooFx on 2012-04-23
> **Toz said:**
> I have a similar setup at work, and to make a long story short, does setting kernel.yama.ptrace_scope to 0 allow the connection?
```
sudo echo 0 > /proc/sys/kernel/yama/ptrace_scope
```

Thanks for your reply.
I still get the same error after inserting that line in the terminal.
The first time I did get Access Denied and after I logged in as superuser I didn't get any response.

---

### Post by Toz on 2012-04-23
Try instead adding:
```
kernel.yama.ptrace_scope = 0
```
to the end of /etc/sysctl.conf and rebooting.

---

