---
title: "limewire share question"
date: 2006-09-21
forum: Desktop Environments
---

### Post by bluefuse on 2006-09-21
I uninstalled frostwire due to the hang-ups it had, slow loading etc... I never had any issues with limewire, so no I return to lime, I want to create a share for lime that everyone can access, but I dont want it saved in any of the users home directory...... how can I create a folder in the /usr/lib/limewire directory and create full unrestricted read/write properties to it?

---

### Post by whizbaby on 2006-09-21
Open terminal
**man chmod**  (manual of command *chmod*)
example (to give rwx-permissions to a folder */foo*)
*sudo chmod 777 /foo*      (octal-mode )
or
*sudo chmod uga+rwx /foo*
(you may want to read the manual of *chown* and *chgrp*,too)

---

