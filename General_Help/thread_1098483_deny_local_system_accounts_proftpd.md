---
title: "deny local system accounts proftpd"
date: 2009-03-17
forum: General Help
---

### Post by stek_87 on 2009-03-17
Hi!

I have an FTP-server set up with proftp and mysql.

How do I _deny_ all local system users to login to proftp and allow all users that I have set up in mysql?

is this possible?

/S

---

### Post by HermanAB on 2009-03-17
Probably not.

Cheers,

Herman

---

### Post by gigahz on 2011-01-24
> **stek_87 said:**
> Hi!

I have an FTP-server set up with proftp and mysql.

How do I _deny_ all local system users to login to proftp and allow all users that I have set up in mysql?

is this possible?

/S

The "AuthAliasOnly on" means you canNOT log in with system users anymore, only aliases.

UserAlias jcarlos1 jcarlos

jcarlos is a real user, and here only "jcarlos1" is a valid user name for ftp.

Now, I don't know how that works with mysql...

---

