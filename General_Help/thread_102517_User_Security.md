---
title: "User Security"
date: 2005-12-12
forum: General Help
---

### Post by GBKevin on 2005-12-12
I have installed Ubuntu 5.1 as a client on Windows 2003 ADS domain.  Everything is working fine except for administrative user permissions on the Ubuntu client.  I would like for my ADS account to have Sudo permissions so that I can run administrative programs on the Ubuntu client using my ADS account.  I receive this error when attmepting to do so:

See Attachment.

---

### Post by localzuk on 2005-12-12
You need to edit the file /etc/sudoers with details of the AD accunt and what permissions it has.

Take a look at 'man sudoers' in a console to find out how to use it.

---

