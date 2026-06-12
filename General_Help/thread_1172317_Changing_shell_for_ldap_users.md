---
title: "Changing shell for ldap users"
date: 2009-05-28
forum: General Help
---

### Post by slyost on 2009-05-28
My users are currently using Sun's workstations authenticated with a SUN LDAP server.  I would like to introduce them into using Ubuntu.  If I change the ldap entry for a user's login shell to /bin/sh from /bin/tcsh, they can login fine to the Ubuntu 9.04 client.  However, I do not want to change this entry for all users since I want them to keep the current shell variable while they are still using the Sun's (there are extensive env variables set for this shell).  Is there a way of changing something in ubuntu (some Xsession or XDM configuration file) so that when a ldap user logs in, their shell is changed to /bin/sh for that session?

---

