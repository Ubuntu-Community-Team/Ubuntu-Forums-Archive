---
title: "sudo or suid?"
date: 2009-02-10
forum: General Help
---

### Post by abracadaver on 2009-02-10
I need to execute the tc (traffic control) from the iproute2 package via some web scripts.  Would it be better to use the suid on tc or add the www-data user to sudoers for tc with no passwd?

TIA,
-Shawn

---

### Post by jbrown96 on 2009-02-10
I would add it to the sudoers file. change ownership to root, and remove the ability for ANY user, including root, to write to the file. SUID should not be used. It can lead to permission escalation.

---

