---
title: "Samba user and password"
date: 2005-12-08
forum: General Help
---

### Post by DrkSn on 2005-12-08
What is the default logon and password for a shared file?  I've tried my user and password but it doesn't work.  It tries to add <my machine>\<username> but even then it doesn't work.

Also on a standard install of Debian the FTPd they use uses the user names as the logon for the FTPd, any idea what its called?

thanks

---

### Post by flopsy on 2005-12-08
Type, in a terminal,

sudo smbpasswd -a yourusername
sudo smbpasswd -e yourusername

Then

smbpasswd

to set the password.

---

