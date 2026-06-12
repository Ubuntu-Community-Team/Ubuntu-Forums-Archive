---
title: "Change Launcher size for all users"
date: 2012-08-15
forum: Desktop Environments
---

### Post by dmouck on 2012-08-15
Hi folks,

I'm setting up some computers at our school that will have multiple users who will authenticate via LDAP. I'm wondering if there's a way to change the Launcher Icon size for everyone to as small as possible (32)? I know how to go into the Appearance setting to change it for a specific user, but how can I change it for everyone?

Thanks in advance!

---

### Post by dmouck on 2012-08-17
Any thoughts at all? In which folder is the default values for users store, such as the Default User profile in Windows? I'd really like to make this change for everyone who will use the system. Thanks!

---

### Post by Krytarik on 2012-08-17
Please see if the method described under "Key File Directories" in this document works:

[https://live.gnome.org/dconf/SystemAdministrators](https://live.gnome.org/dconf/SystemAdministrators)

In your case, the needed key file should look like this:
```
[org/freedesktop/compiz/unityshell]
icon-size=32
```Regards.

---

### Post by dmouck on 2012-08-24
Thanks much, Krytarik! I believe this will do the trick.

---

### Post by Homer on 2012-11-13
Hello,

I want to do the same thing, but with no success.

The /etc/dconf directory doesn't exists.  Is it normal?  I created it, but I'm unable to make to change the launcher default size.

Thanks.

---

