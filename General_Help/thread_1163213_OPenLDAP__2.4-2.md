---
title: "OPenLDAP  2.4-2"
date: 2009-05-18
forum: General Help
---

### Post by anand.sandesh on 2009-05-18
Hi, I am a nOOB and was trying to install OpenLDAP 2.4-2 on Ubuntu 8.10. I only have ssh access to it (its a remote server).

I did the stuff in this tutorial
[https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.10/serverguide/C/openldap-server.html)

I am stuck at the point where we need to populate the directory.

I get this error
ldap_bind: Invalid credentials (49)

There is no slapd.conf.. hence I do not know how to get the details of my rootdn is etc..

Also, what does this mean?

There should now be a *dn: cn={4}misc,cn=schema,cn=config* entry in the cn=config tree.               

where exactly should I look.

any help wil be appreciate.

Yours
n00b Sandesh

---

