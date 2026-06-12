---
title: "Winbind, and samba"
date: 2005-10-15
forum: Desktop Environments
---

### Post by MikeyXX on 2005-10-15
So I'm following [Wiki thingy]("https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto") and I'm was able to run the "net ads join" and I get:

Using short domain name -- ANITTEB
Joined 'DELLLT' to realm 'ANITTEB.COM'

Then the How To says to run wbinfo -u to get a list of users, but I get this:

Error looking up domain users

What can this be? Next step says to test the nsswitch with getent passwd and you should see new users in the list in the domain you joined. But I don't get those.

---

### Post by jworr on 2005-12-22
I am having the same problems and I don't know what to do.  If I find anything I will post it here

---

