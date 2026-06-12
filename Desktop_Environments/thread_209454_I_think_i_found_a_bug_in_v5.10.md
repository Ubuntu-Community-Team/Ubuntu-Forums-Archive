---
title: "I think i found a bug in v5.10"
date: 2006-07-05
forum: Desktop Environments
---

### Post by R2D2-Master on 2006-07-05
Can someone confirm please.

I type in the folowing command.

sudo smbpasswd -a xxxxxxx

it then asked the folowing questions.

Password:
Samba Password:
Retype Samba Password:

i type in the folowing.

Password:  Which is supposed to be the supervisor password, i type the users password by accident.
Samba Password: i retype users password.
Retype Samba Password: I realised my fault and just entered through it didn't change the samba password because samba password didn't match.

But the problem is it changed my sudo password to the users samba password. I needed to ask the user what her password was to get into the Users Program to change the password back.

Thanks

---

### Post by hayesey on 2006-07-05
"sudo" asks for the user password, not the root password so that seems right to me. 

A quote from the sudo "man" page:

> sudo requires that users authenticate themselves with a password by default (NOTE: in the default configuration this is the
       user&#8217;s password, not the root password)

---

