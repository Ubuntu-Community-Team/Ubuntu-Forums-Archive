---
title: "browsing Samba shares?"
date: 2009-06-21
forum: General Help
---

### Post by Mewshi on 2009-06-21
Hey everyone!  I'm trying to find a way to browse samba shares.

First off, the computers don't seem to be seeing each other.  Second, Nautilus is being a whiny little girl about network browsing.  Any help will be appreciated ^-^

---

### Post by credobyte on 2009-06-21
Are they on the same "workgroup" ?

---

### Post by swerdna on 2009-06-22
> **Mewshi said:**
> Hey everyone!  I'm trying to find a way to browse samba shares.

First off, the computers don't seem to be seeing each other.  Second, Nautilus is being a whiny little girl about network browsing.  Any help will be appreciated ^-^

There's a couple of steps:
[LIST=1]
[*]check that the Samba daemons are running with this terminal command:```
sudo /etc/init.d/samba status
```and check the samba confg file with this command```
testparm
```
[/LIST]
From the Samba config file look for these lines:
[LIST]
[*]name resolve order = bcast host lmhosts wins 
[*]workgroup = etcetcetc
[/LIST]
make the workgroup the same as windows machines.

If there are any questions, please ask and at the same time post here the return you get from "testparm".

---

### Post by Wiebelhaus on 2009-06-22
Strangely I've noticed since 9.04 that manually editing the samba config file seems to damage samba rather than configure it , I'd normally go through the process of explaining how it functions and what changes need to be applied but something has changed and I'm not sure what it is yet.

---

### Post by swerdna on 2009-06-22
> **Wiebelhaus said:**
> Strangely I've noticed since 9.04 that manually editing the samba config file seems to damage samba rather than configure it , I'd normally go through the process of explaining how it functions and what changes need to be applied but something has changed and I'm not sure what it is yet.

That's odd. I haven't experienced that. Let us know if you find out what's affecting your installation.

---

