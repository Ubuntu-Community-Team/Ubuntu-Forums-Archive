---
title: "Diff' between creating a new user in shell and GUI"
date: 2006-05-07
forum: Desktop Environments
---

### Post by hldub on 2006-05-07
I am trying to write a script that creates a new user and sets up some other services for this user (samba amongst others).  When I use either the adduser or useradd command in the shell a user is added but when I log in to the account the system doesn't behave correctly (sound problems, no auto-mounting of removable storage etc). I do not have the same problem when I create a user using System-Administration-Users & Groups...

Can anyone help please?

---

### Post by aysiu on 2006-05-07
Make sure you add your user to these groups: ```
adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
```

---

### Post by hldub on 2006-05-08
Thankyou, that makes sense.

---

