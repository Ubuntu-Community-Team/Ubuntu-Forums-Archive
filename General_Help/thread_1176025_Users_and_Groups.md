---
title: "Users and Groups"
date: 2009-06-01
forum: General Help
---

### Post by measekite on 2009-06-01
What do I have to do when I user Users and Groups to create users that have the same menu system, panels and access to the same applications?

I do not see a menu option for that nor do I know what files if any to edit.

---

### Post by capscrew on 2009-06-01
There are global settings for all users.  These are called skel files.  The skel files located at /etc/skel/ and are hidden files. You need to use *ls -la* from the command line to see them or cntl-h when using Nautilus.

These skel files hold the default settings for all users.  The user can then add their own personal configuration files.

---

