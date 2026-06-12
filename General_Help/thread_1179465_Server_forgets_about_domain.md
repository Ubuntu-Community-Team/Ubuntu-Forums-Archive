---
title: "Server forgets about domain?"
date: 2009-06-05
forum: General Help
---

### Post by Megalomania on 2009-06-05
I'm running Server 9.04 on a fairly standard machine (i7 920, 4 GB ram, nothing special) joined to a Windows Server 2008 domain.  Samba connected initially like a dream and every was set up great.  However, recently after being up for a few days to a few weeks, the server just stops doing anything with the domain itself - files are no longer registered as belong to domain\user (only ID numbers are displayed when I ls -l), if I left a session running on my domain account, "whoami" tells me that I don't exist, and I can not log in with domain logins.

Restarting samba does nothing to fix it, and all that works is restarting the server (after which it boots up and recognizes the users and files just fine).  A VM on another server running the same services and OS has never had this issue, and I have no idea where to even start looking for the problem apart from where I already have.

---

