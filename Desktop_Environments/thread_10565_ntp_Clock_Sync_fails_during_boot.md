---
title: "ntp Clock Sync fails during boot"
date: 2005-01-09
forum: Desktop Environments
---

### Post by iminj on 2005-01-09
During the boot sequence, I'm getting a message that "synchronize clock to ntp.ubuntulinux.org" is failing. I am getting the network interface "OK" prior to this step.

Anyone else noticing this; and any ideas how to resolve?  Is Ubuntu's ntp server down? If so, how does one edit the boot instructions to connect to an alternate ntp server?

Thanks - iminj

---

### Post by DonScorgie on 2005-01-09
I'm getting that too.  Not sure when it started, but it aint working now.

A manual attempt to synchronise leads to:
$ sudo ntpdate ntp.ubuntulinux.org
 9 Jan 14:07:39 ntpdate[10192]: no server suitable for synchronization found

So I'm guessing its a problem with the server (Only a guess mind)

You can change the ntp server your connecting to in 
/etc/default/ntpdate
Just comment (#) out the line
NTPSERVERS="ntp.ubuntulinux.org"
and add a different server.

Don

---

### Post by iminj on 2005-01-09
[QUOTE=DonScorgie]
You can change the ntp server your connecting to in 
/etc/default/ntpdate
Just comment (#) out the line
NTPSERVERS="ntp.ubuntulinux.org"
and add a different server.

Don[/QUOTE]

Thanks for the assistance. 

I edited /etc/default/ntpdate, and inserted an ntp server that's physically closer to my location. When I rebooted, the bootup clock sync step was problem-free.

I think we can conclude that the Ubuntu ntp server is not operating.

-iminj

---

### Post by wallijonn on 2005-01-21
Thanks, Dan.

---

