---
title: "Add/Remove programs missing"
date: 2009-04-26
forum: General Help
---

### Post by dodgem on 2009-04-26
I know there are a few other threads on this, but i haven't found anything there that helps...

I have logged in as a user authenticated by an ldap db on another machine.  The user on the remote server has a primary group of the same name and id as the user, and is also a member of users(100) and admin(121).

Without being in the admin group i couldn't use sudo on the machine i've  logged into (as expected), however, despite being in the admin group and able to sudo, the Add/Remove Programs option is missing from the Applications menu.

If i try and edit the Apps menu then a second after checking the box next to Add/Remove Programs, it unchecks itself - as would happen if you weren't in the sudoers list.  I've tried adding the user to the sudoers list on the local machine but still to no avail, and that wouldn't be an ideal situation anyway as it would prevent central changes to the users admin rights being made.

Any ideas on how to get the Add/Remove Programs button back for a user logged in via ldap?

Oh, and incase it makes a difference, the ldap server is running on CentOS, not Ubuntu.

Thanks.

---

