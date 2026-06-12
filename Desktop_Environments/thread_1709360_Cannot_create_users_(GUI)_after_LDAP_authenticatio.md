---
title: "Cannot create users (GUI) after LDAP authentication installation"
date: 2011-03-18
forum: Desktop Environments
---

### Post by Jean-Michel C. on 2011-03-18
Hi there,
after quite a bit of tampering, I finally have LDAP working on my (10.10) server and now trying to have the authentication working on the client.

I followed the process described [here]("https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html#openldap-auth-config") and I have defined a user in LDAP (at the ["populating LDAP" stage]("https://help.ubuntu.com/10.10/serverguide/C/openldap-server.html#openldap-server-populate")).

When switching to my 10.10 **desktop**, I was unable to log in with the credentials of the user defined in LDAP.

I thought that it might be because the user (and home directory) did not exist locally and I tried to create it (the user).

So when I click "Add new user" in the GUI "User & Group management" application (might not be exactly that, my install is in French), I am asked for my password, in the new user window, I input name and login, and when I click "save", an error window tells me that I have insufficient privileges...

There is nothing obvious (nothing at all at that time actually) in /var/log/syslog or /var/log/auth.log.

Any idea in what direction I should dif?

Many thanks in advance.

---

