---
title: "Some help with user accounts and domain restrictions"
date: 2009-03-18
forum: General Help
---

### Post by darkman738 on 2009-03-18
Ok, so I have a domain at work, and a majority of the computers are running Windows.  There is a domain setup with a Windows server.  I have a Linux box for certain things we need to do, running Ubuntu 8.10.  I have installed Likewise Active Directory, and have the computer joined to the domain.  I can access the shares as normal, everything seems to be fine.  The only problem is that sever of the accounts, who are not admins, occasionally need sudo access to the terminal for certain apps.  The problem is that I can't seem to figure out how to give them sudo rights without making them an admin on the network, which I'm not going to do.  When I try "sudo -i" or w/e at the Terminal, it tells me that the accounts is "not a sudoer" and "the incident will be logged." In Windows I would simply add there user account as an admin to there local machine, is there a way to accomplish the same effect Ubuntu?  I have no problems with them having admin/root access on there local machine, but I don't want to give them global access rights to the network.  I'm am not an Ubuntu expert by any stretch so please forgive me if I have the wrong terminology on anything here.  I hope that is clear enough.

---

### Post by darkman738 on 2009-03-18
Well I found the answer if anyone ever runs into this.  If anyone is intrested login as either a network or local admin, open terminal:


```
sudo visudo
```

when the editor pops up scroll down to the 

```
# User privilege section
```

and add 

```
DOMAIN\\USER ALL=(ALL) ALL
```

the "\\" is important.

Hopes this helps.  You can customize what each user has sudo access for, search visudo for more info, it can get semi complex, very customizable.

---

