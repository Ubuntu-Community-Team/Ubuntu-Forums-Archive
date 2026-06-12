---
title: "network logins and samba"
date: 2005-12-15
forum: General Help
---

### Post by linrasta on 2005-12-15
I hope this question doesn't offend anyone, but realize I am in the transition process from winblows to ubuntu.  Here is the question:  In a professional environment, most computers require a login, and without it, the computer cannot be used.  A lot of times, the computers will go to the server to verify login information, and also a lot of times, information that is stored on the server is now available to the user, regardless of which machine they login on.  What is this type of setup called? I have read a little about WINS, is this the service that does all of this? Is samba used to provide this service? How can I do this at home? Thanks for helping a lame brain noo-b!

---

### Post by alamba on 2005-12-15
Yep buddy. Samba it is. PAM authentication is what u're looking for. Google on it and you'll find a number of howto's on how to set this up. You can not only authenticate the user centrally but also setup his home directory on the file server and map it to the machine he's using on the fly.

Forget WINS. Its windoze legacy naming service if i'm right (and i might not be).

Akshay

---

### Post by schilcha on 2005-12-15
If you're setting up a linux/unix-only environment, I would rather use yp/nis (yellow pages / network information service?) for authentication and nfs for distributing home-drives. These do nicely integrate into the system (opposed to samba, which has to do some tricks to join linux and windows).

---

