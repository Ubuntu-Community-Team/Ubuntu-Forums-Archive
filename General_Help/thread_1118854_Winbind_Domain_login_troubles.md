---
title: "Winbind Domain login troubles"
date: 2009-04-07
forum: General Help
---

### Post by ohkay on 2009-04-07
Hi, I'm setting up an Ubuntu 8.10 workstation that needs to have domain login. I am using Winbind and I have installed and configured everything that is necessary, but I am having issues with certain domain accounts. I can login to the Ubuntu workstation with an account that is setup to be an administrative account on the domain (it is a member of certain groups that have admin privs on the Windows machines that are also on the domain). However, when I try to login on an account that is setup to be an normal user account, the system tells me the username and/or password are bad. In the auth.log file, I get this message for the normal user (the one that doesn't work):

Apr  2 10:55:31 Linux-Lab gdm[4777]: pam_winbind(gdm:auth): getting password (0x00000000)
Apr  2 10:55:35 Linux-Lab gdm[4777]: pam_winbind(gdm:auth): user 'domainuser' granted access
Apr  2 10:55:35 Linux-Lab gdm[4777]: pam_unix(gdm:account): could not identify user (from getpwnam(domainuser))

and I get this message for the admin user (the one that works):

Apr  2 11:02:50 Linux-Lab gdm[4777]: pam_winbind(gdm:auth): getting password (0x00000000)
Apr  2 11:02:54 Linux-Lab gdm[4777]: pam_winbind(gdm:auth): user 'domainadmin' granted access
Apr  2 11:02:54 Linux-Lab gdm[4777]: pam_winbind(gdm:account): user 'domainadmin' OK
Apr  2 11:02:54 Linux-Lab gdm[4777]: pam_winbind(gdm:account): user 'domainadmin' granted access
Apr  2 11:02:54 Linux-Lab gdm[4777]: pam_unix(gdm:session): session opened for user domainadmin by (uid=0)

Anyone have any ideas as to what's going on with my normal user account? Any fix suggestions would be awesome.

---

