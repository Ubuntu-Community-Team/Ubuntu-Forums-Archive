---
title: "Need help with Ubuntu, likewise-open and active directory"
date: 2009-01-19
forum: General Help
---

### Post by bradthegreat on 2009-01-19
I currently work at a large public school. I am working on a project to replace Windows with Linux in 5 labs, roughly 150 computers. We run Active Directory with LDAP and the whole shebang. I was able to use Likewise-Open to add my Ubuntu machines to the domain and can successfully log in. I found a work around for mounting student folders as libpam did not work quite right.

my issue is this: I can log into the machine and it takes roughly one minute to get a desktop up and rolling. When I log in with a student account, it will take a minimum of 3.5 minutes to get everything up. Sometimes I've clocked it at 10 minutes. I think the problem rests with one particular group that all students are a part of. Is there any way to make Ubuntu reject Active Directory group membership as I think that group is causing the login to take forever? If I remove the group, the login time usually goes to under a minute. I can't remove the group from everyone as that would screw up the rest of the Windows PC logins. I have been beating my head on the desk for weeks now and have run into a wall here. Any help would be much appreciated!

---

