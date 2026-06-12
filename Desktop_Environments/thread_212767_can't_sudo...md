---
title: "can't sudo.."
date: 2006-07-10
forum: Desktop Environments
---

### Post by nismohasan on 2006-07-10
i was following the guide to getting firestarted to start up on gnome bootup but now i can't seem to use sudo.. stupid me should of relized that it was a system service and i didnt need to do this.. now i pay for it lol..

> hasan@nismo-oobuntoo:~$ sudo aptitude upgrade
sudo: /etc/sudoers is mode 0600, should be 0440


what can i do to fix this?

no sudo commands work at all.

---

### Post by taurus on 2006-07-10
See if you belong to groups adm & admin with this command.
```

id

```
And if you are not, then you need to add yourself to those two groups in /etc/group...  Since you can sudo, it means you must boot your Dapper with the recovery mode (from GRUB menu) and edit it as
```

nano /etc/group

```

---

### Post by nismohasan on 2006-07-10
my username is listed when i type id in terminal, i believe the error has something to do with the file permissions (number view for sudoers is 600 like the error says, its meant to be 440 but i cant change it?_

---

### Post by taurus on 2006-07-10
Not username!  What groups do you belong to???  If not sure how to read it, just paste the output here then...

---

### Post by nismohasan on 2006-07-10
i fixed the problem by rebooting to recovery mode then changing the chmod from there. "chmod 440 sudoers" and it fixed the problem cheers :)

---

