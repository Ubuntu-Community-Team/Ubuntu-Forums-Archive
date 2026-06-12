---
title: "Trouble with one user logging into a machine via LDAP"
date: 2007-04-10
forum: Desktop Environments
---

### Post by markusfarkus on 2007-04-10
Hello I am having troubles with a user logging into a machine.  It is giving me this error:
Your $HOME/.drmc file has incorrect permissions and is being ignored. This prevents the session from being saved. File should be owned by user and have 644 permissions.

I am running an LDAP server to authenticate the user and NFS to redirect the home dir to a file server.  It doesn't seem to be a universal problem at all.  He cannot ssh or vnc or log locally into the machine.  Of course I tried everything that the error message wants me to try.  

I saw several people mention that you might try changing permissions to 600 and that seemed to work for some.  I also found some that said they changed the entire home dir to 700.  None of that has helped me out. I don't believe most of those posts included the LDAP or NFS that I am doing.

I have also deleted and recreated the user already to try and fix this problem.  Does anyone have any ideas that might be able to help me?

Thanks, :confused:

---

### Post by markusfarkus on 2007-04-11
Does anyone have any suggestions for this problem?

---

### Post by HornedBeast on 2008-01-28
Im having general problems using LDAP logins and remote home folders. sometimes when I try and logout, the account and client computer just hang.

Also, I found that the users that are logging in with LDAP on Gnome cant access hardly anything, including volume controls and things. How do I setup the user permissions in the LDAP directory to be allowed access to these basic things that a usual user on an Ubuntu Gnome Desktop get?

---

