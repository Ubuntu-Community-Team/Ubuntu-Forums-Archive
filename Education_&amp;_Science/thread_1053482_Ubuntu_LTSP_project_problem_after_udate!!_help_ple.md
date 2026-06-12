---
title: "Ubuntu LTSP project problem after udate!! help please"
date: 2009-01-28
forum: Education &amp; Science
---

### Post by thomsany on 2009-01-28
Hi!!
My Ubuntu 7.10 Server ran some updates last night and installed a Sieve program which uses port 2000 which was used by the LTSP project used to connect my thin clients to the network.
After I restarted the server after the update, no client was able to access its interface.
Looks like the Sieve or whatever program that installed on the server update blocked port 2000 or is using it for some reason!
I would like to make sure port 2000 is always used for the LTSP thin clients.
How can I remove the port usage of Sieve and leave it to LTSP?
Please help me since my network is down due to this.

Any suggestions?

Thanks much in advance,
Teo

---

### Post by freerkkalsbeek on 2009-02-19
Hi Teo,

There are two (or actually 3) options:
1. Remove the package that uses the sieve port
2. Change the config for the sieve package to us an alternate port (Not recommended)
3. Change your LTSP configuration so that it uses a different port (For instance 9573)

I prefer option 3.
What you need to do is:
- update /etc/inetd.conf and change the portnumber for nbdrootd
- restart openbsd-inetd /etc/init.d/openbsd-inetd restart
- run ltsp-update-image

The last one will make sure your nbdport is propagated to PXE. (/var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default
example: DEFAULT vmlinuz ro initrd=initrd.img quiet splash nbdport=9573

After that, your LTSP clients should boot again, using the new port for nbdroot

Hope this is still in time to fix your problem, but at least it might help others that run into the same issue.

Regards,
Freerk

---

### Post by freerkkalsbeek on 2009-02-19
Or even simpler:

run ltsp-update-image -p xxxx
This will do everything needed to make nbdrootd run on port xxxx and your thinclient connecting to it.

Freerk

---

