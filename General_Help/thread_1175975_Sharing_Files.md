---
title: "Sharing Files"
date: 2009-06-01
forum: General Help
---

### Post by measekite on 2009-06-01
There are five users on a network.  A thru E.  E wants to share his home folder but only want to share it with A and B but not C and D.

How can E share his files so that they are password protected where C and D cannot see them without a password but A and B who have the password can either read or write depending on permisssions?

---

### Post by Iowan on 2009-06-01
Are the users logging onto the computer, or accessing it via other machines? What OS(s) is/are involved?

---

### Post by measekite on 2009-06-01
> **Iowan said:**
> Are the users logging onto the computer, or accessing it via other machines? What OS(s) is/are involved?

All users have their own machines running Ubuntu.  There is also a network server running Windows but I am not concerned with that.

There must be a way so that the user must enter a password to see the share.

I know in Windows you can password protect your share and only those with the password can see it.

---

### Post by aeiah on 2009-06-01
two main ways to do this would be to 

a:
set up NFS and add the usernames to a list of users allowed to access and write to the share. you could probably do it on a hostname basis instead or as well as username.

b:
set it up as an ssh network location. they could log on to the ssh target with the target computer's password or as a username/password you've set up on the target specifically. you could also use pre-shared keys instead of passwords, essentially limiting it on a per-user basis with no login prompt required. of course, if you actually want this to be secure from the inside, ie, you have nerdy kids that want to cause mischief, then they could always steal the pre-shared key if they find a computer that's currently logged on.

both methods should be secure from the outside world though.

and then i suppose there's option c: samba. this might be useful if you do want to get windows involved in things, but its a lot more complicated and often best just configured alongside other methods, existing just to allow windows integration.

---

### Post by t0p on 2009-06-01
You could use **Truecrypt** to create an encrypted directory.  Tell your friend the password and he can access the directory's contents.  The other guys won't be able to get at it.

Truecrypt is in the repos, I believe.

---

