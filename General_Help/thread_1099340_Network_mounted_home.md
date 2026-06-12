---
title: "Network mounted home?"
date: 2009-03-18
forum: General Help
---

### Post by muxecoid on 2009-03-18
Hello. I have 3 computers connected via a simple network switch. I want the first computer to hold /home/ and the other two to see it as their own /home/ as well. The disks of other two computers should also be shared and have the same path on all 3 machines. Also I want it to be transparent between the 3 machines but not mountable/accessible from other computers. Any advice?

---

### Post by ugm6hr on 2009-03-18
> **muxecoid said:**
> Also I want it to be transparent between the 3 machines but not mountable/accessible from other computers. Any advice?

I'm not sure if this is possible with any file sharing protocol.  The shares are either open within the network, or use passwords.

Apart from this, NFS will allow you to mount a network directory as /home and allow directories on any machine to be mounted similarly (e.g. in /media/comp1 and /media/comp2) from fstab.

[https://help.ubuntu.com/8.10/serverguide/C/network-file-system.html](https://help.ubuntu.com/8.10/serverguide/C/network-file-system.html)

---

### Post by nelskurian on 2009-03-18
May be it can be done through NFS....i am not try it any way..may be theirs permission issues...go for a break...:D

---

### Post by muxecoid on 2009-03-18
The computer is connected to other 2 through eth0 and to the organization-wide LAN through eth1. Is it possible to achieve what I need by playing with subnet masks?

---

### Post by heindsight on 2009-03-18
> **muxecoid said:**
> Hello. I have 3 computers connected via a simple network switch. I want the first computer to hold /home/ and the other two to see it as their own /home/ as well. The disks of other two computers should also be shared and have the same path on all 3 machines. Also I want it to be transparent between the 3 machines but not mountable/accessible from other computers. Any advice?

I'm not sure I understand what you mean by "transparent between the 3 machines". However, as already mentioned by others, you can use NFS for this. NFS does allow you to specify exactly who is allowed to mount an exported directory. 

For example if host1 should export /home/ then you would add an entry to /etc/exports on host1 to specify that /home should be accessible to host2 and host3. There are various ways in which you could specify the machines that are allowed to access an exported directory, including listing individual host names or IP address/netmask pairs. Have a look at the manual for exports file for more details about this:
```
man exports
```
Or:
[http://manpages.ubuntu.com/exports.5.html](http://manpages.ubuntu.com/exports.5.html)

---

### Post by geirha on 2009-03-18
This guide uses /home export as an example: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

