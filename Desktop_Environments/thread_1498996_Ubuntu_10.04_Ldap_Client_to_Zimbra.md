---
title: "Ubuntu 10.04 Ldap Client to Zimbra"
date: 2010-06-01
forum: Desktop Environments
---

### Post by elzwhere on 2010-06-01
We are currently upgrading our systems from ubuntu 9.04 to 10.04. We've been using zimbra as our ldap server for quite some time now and I've noticed something very strange on how 10.04 wants to authenticate to the zimbra ldap server. 

Ldap authenticaion works fine as a regular user.  The problem that we're having is that for some reason with 10.04 if a user is considered an admin in the ldap db that they do not need a password to log in.  This is not the case with 9.04 or 9.10. From what I can tell the nsswitch / ldap.conf files are identical from previous releases.  We have not updated Zimbra at all so I know there was no change there.  

Has anyone else ran into this issue?  Or does anyone else have any ideas what has changed in the new release regarding authentication to ldap server?

---

