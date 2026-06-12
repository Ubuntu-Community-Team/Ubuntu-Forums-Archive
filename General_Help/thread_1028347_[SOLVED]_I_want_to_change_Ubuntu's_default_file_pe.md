---
title: "[SOLVED] I want to change Ubuntu's default file permissions"
date: 2009-01-02
forum: General Help
---

### Post by engocoka on 2009-01-02
I'm planning on setting up a multi-user ubuntu server where users have shell access to this machine.  I notice the default file permissions on ubuntu seem to be 644 for files and 755 for directories.

Is there a way to change the default file/directory permissions to 600 and 700 respectively?

---

### Post by taurus on 2009-01-02
All you have to do is change the permissions of the $HOME for each user to 700.  Then, nobody can view or access somebody else's $HOME.

---

### Post by engocoka on 2009-01-02
> **taurus said:**
> All you have to do is change the permissions of the $HOME for each user to 700.  Then, nobody can view or access somebody else's $HOME.

Thanks for the reply.  I would prefer some automatic solution as opposed to just chmoding the home directories.  For example, users may want their home directories readable/executable to host their local webpage.  If they want to do this, they should be allowed to set the appropriate permissions themselves.  However, I'd like to avoid inexperienced users creating new files and directories that are world readable without knowing what they're doing.

Is there any way to change a setting such that new files and directories are created without world readable/executable permissions?

---

### Post by engocoka on 2009-01-02
The solution I found was to change my umask command in /etc/profile from

```
umask 022
```
to


```
umask 077
```

---

