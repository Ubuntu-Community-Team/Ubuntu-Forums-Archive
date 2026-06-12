---
title: "[SOLVED] Konqueror smb automatic authentication"
date: 2008-03-12
forum: Desktop Environments
---

### Post by teamanx on 2008-03-12
Hi. I know that Konqueror can use the credentials of the currently logged in user, to connect to samba shares, so it doesn't prompt for username and password. I have made it work on a couple of computers, but I don't know how I did it. :(
Anybody knows how to do it?

Thanks!

---

### Post by dark_phantom on 2008-03-13
~/.smbpw:
username="id"
password="pw"

At least that's how I was able to do it.  Although I use the command line to mount a samba share.

---

### Post by teamanx on 2008-03-13
Well, I have been searching and realized that konqueror is able to use kerberos tickets to authenticate against samba. So if you logged in via pam_krb5, konqueror will use your credentials to access samba shares. It is the same that "smbclient -k".

---

