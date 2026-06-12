---
title: "ldapmodify Freezes"
date: 2009-06-21
forum: General Help
---

### Post by jogrady on 2009-06-21
I'm working through the LDAP configuration tutorial and ran into a problem.  Any time I use a idapmodify command I'm prompted for a password and when I enter the correct one nothing happens.

Here is what I see:

jogrady@ogradyhq:/$ ldapmodify -x -D cn=admin,cn=config -W
Enter LDAP Password:
|

Here is the link to the step I'm trying complete.

[https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html#openldap-tls]("https://help.ubuntu.com/9.04/serverguide/C/openldap-server.html#openldap-tls")

I'm using 9.04 AMD 64 server addition.

---

### Post by jogrady on 2009-06-22
No reply?  I'm a relatively new user and have noticed a lot of threads not getting responded to.

---

### Post by dr_latino999 on 2009-10-19
I'm going to bring this back up, as I am too now experiencing the same problem. I do not know if you have managed to rectify this situation, but I'm hoping someone who has run into it before will be able to shed some light on this.

---

### Post by timharne on 2009-10-20
I hope the server 9.10 fix the issue with the ldapmodify freezing.

---

