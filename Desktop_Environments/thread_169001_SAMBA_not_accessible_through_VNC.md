---
title: "SAMBA not accessible through VNC"
date: 2006-05-01
forum: Desktop Environments
---

### Post by minky on 2006-05-01
Hi , 

I am new to the group and hope its going to be helpful.I have newly joined as a System Admin so I don't have a lot of experience doing this stuff.
I am running CentOS 4.0 on various machines and the similar one on the server which hosts SAMBA.When I try and VNC into it from windows XP(on a shared Novell network) or other Linux clients,SAMBA does not open up and neither does NFS.However it is running fine on the server.I am contemplating it might be a security/firewall problem but am not sure because all windows/linux machines here talk to each other via VNC.I am unable to come up with a resonable solution.PLease advise..
thanks in advance
Minky

---

### Post by elamericano on 2006-05-02
If you are using a remote desktop that logs in a new user, I could see a permissions problem, but if you're successfully accessing the desktop of an open session, I can't see how there can be any difference.

When VNC is connected, can you still access the shares from the server locally?

By the way, if you don't get a satisfactory answer here, it may be because you are using CentOS, and we all use Ubuntu. Maybe you should run this by a group of CentOS users for best results.

---

