---
title: "login screen"
date: 2013-05-09
forum: Desktop Environments
---

### Post by morphyrichards1 on 2013-05-09
How can I stop edubuntu from displaying a list of local users on the login screen ?
I want to be able to type in a username and password for ldap users instead.

Thanks

---

### Post by Cheesemill on 2013-05-09
```
sudo /usr/lib/lightdm/lightdm-set-defaults --hide-users true
sudo /usr/lib/lightdm/lightdm-set-defaults --show-manual-login true
```
Should do the trick.

---

