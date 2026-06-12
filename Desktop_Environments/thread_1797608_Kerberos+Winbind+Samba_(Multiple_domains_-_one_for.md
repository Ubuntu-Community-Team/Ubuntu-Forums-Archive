---
title: "Kerberos+Winbind+Samba (Multiple domains - one forest)"
date: 2011-07-05
forum: Desktop Environments
---

### Post by robert_wolu on 2011-07-05
Dear all
We have a master domain with a child domain in the same forest. The situation is that all users’ accounts are in the master domain and the computers are in the child domain.
Let assume following:
MASTER.DOMAIN.COM – is the master domain with few KDC. Users’ object sits here.
CHILD.DOMAIN.COM – this is where the computer account sits.
Here is what I am trying to do.
I would like to join my Linux hosts (Centos/Ubuntu) to the Windows Active Directory system. Ideally this should include: SSH logon (openssh), Samba, and system logon.
So far I identified that I need to configure Kerberos and samba in the right way so I will be able to join the system to the domain. That however after many attempts has not been successful due to as I believe complexity of this configuration.
I am wondering if someone have similar arrangement and possibly have a working solution.
Ps. I am looking for opensource solution and I tried already Likewise
With regards 
Rob

---

