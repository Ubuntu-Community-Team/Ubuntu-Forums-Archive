---
title: "sudo problem"
date: 2006-06-08
forum: Desktop Environments
---

### Post by mauriced on 2006-06-08
Hi
When using sudo -i to log in as root I receive the following message:
sudo: /etc/sudoers is mode 0442, should be 0440
Also I can no longer use update manager.  Any help to fix this problem would be gratefully accepted.
Maurice

---

### Post by frying_fish on 2006-06-08
quick fix is to reboot in rescue mode and change the permissions of the file to the ones it wants (so chmod 440 /etc/sudoers), that should solve the problem quickly.

---

### Post by mauriced on 2006-06-08
Hi
Thanks for that, your fix worked a treat. Up and running again.
Maurice

---

### Post by mortsahl on 2006-06-08
Probably blasphemy, but, why not ...

sudo passwd root

then just BE root instead of all the SUDO bs?

---

