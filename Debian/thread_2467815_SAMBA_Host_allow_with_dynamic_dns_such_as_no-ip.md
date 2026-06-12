---
title: "SAMBA Host allow with dynamic dns such as no-ip?"
date: 2021-10-08
forum: Debian
---

### Post by egd4 on 2021-10-08
Hi, 
First, excuse my english, i'm french :)

For test purposes, i had to install a samba server on a distant server for work. Everything works fine.
My  issue is to deal with access restrictions: I use "host allow" command  in the smb.conf, wich works fine when I use my client ip address, but  client ip address change frequently. I had the idea to use a dyndns such  as "no-ip" to retrieve changing ip with an http factor.
But it seems  that "host allow" option from samba does not resolve the ip with that  factor, although he recognize it. here is an extract of the log where it  recognize my connection (replaced some infos by x): 

In my smb.conf:

hosts allow = xxx.ddns.net

[2021/10/08 16:08:09.519621,  0] ../source3/lib/access.c:338(allow_access)
  Denied connection from areims-xxx-x-xx-xx.w90-7.abo.xxxxxxx.fr (90.x.x.99)

the ip that semba regognize is the right one, but deny the access... 

Someone could help with a hint?
Thanks in advance

---

### Post by ActionParsnip on 2021-10-08
I don't suggest you expose Samba to the internet. It's a really bad idea.
Are you using Samba for authentication, file sharing or both please?
What is the output of:
```

lsb_release -a
uname -a
dpkg -l | grep -i samba

```
Thanks

---

### Post by egd4 on 2021-10-08
I've already been told this, but this is the only protocol recognized by the software i intend to use with...
I'm using it for file sharing, not sure what you mean with authentication?

The output for your cli code is:


No LSB modules are available.
Distributor ID: Debian
Description:    Debian GNU/Linux 8.5 (jessie)
Release:        8
Codename:       jessie



Linux ns3045576.ip-94-23-25.eu 3.14.32-xxxx-grs-ipv6-64 #7 SMP Wed Jan 27 18:05:09 CET 2016 x86_64 GNU/Linux




ii  libwbclient0:amd64             2:4.2.14+dfsg-0+deb8u13      amd64        Samba winbind client library
ii  python-samba                   2:4.2.14+dfsg-0+deb8u13      amd64        Python bindings for Samba
ii  samba                          2:4.2.14+dfsg-0+deb8u13      amd64        SMB/CIFS file, print, and login server for Unix
ii  samba-common                   2:4.2.14+dfsg-0+deb8u13      all          common files used by both the Samba server and client
ii  samba-common-bin               2:4.2.14+dfsg-0+deb8u13      amd64        Samba common files used by both the server and the client
ii  samba-dsdb-modules             2:4.2.14+dfsg-0+deb8u13      amd64        Samba Directory Services Database
ii  samba-libs:amd64               2:4.2.14+dfsg-0+deb8u13      amd64        Samba core libraries
ii  samba-vfs-modules              2:4.2.14+dfsg-0+deb8u13      amd64        Samba Virtual FileSystem plugins

---

### Post by coffeecat on 2021-10-08
*Thread moved to **Debian** sub-forum.*

---

### Post by Tadaen_Sylvermane on 2021-10-13
Can you use sshfs to mount the remote location locally? Then just use it like any other local files stem. Sure safer than Samba

---

