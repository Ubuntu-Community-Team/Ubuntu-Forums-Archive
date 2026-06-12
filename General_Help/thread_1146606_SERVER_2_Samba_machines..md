---
title: "SERVER: 2 Samba machines."
date: 2009-05-02
forum: General Help
---

### Post by Tux.Ice on 2009-05-02
Alright, here goes nothing:

I have 2 servers, server1 and server2, both run Ubuntu Server 8.10 w/o a GUI, and Samba.

I have server1 setup to accept domain logons, and to authenticate users and point their H: drive to their home directory. As this was getting slow once we got about 20 users, I set-up another server, server2, how can I do the following:

Have server1 accept the domain logon, and map H: to the users home directory whil having users 1 through 5 home directorys be on server1 and users 5 through 10 home directorys be on server2, while having only 1 domain called DOMAINA.

How would I setup samba to decide where to find the users roaming profile and home directory?

If it makes any difference, I'm running Windows XP clients :)

Help appreciated,
Adam

---

### Post by Tux.Ice on 2009-05-02
Bump.

---

