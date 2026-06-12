---
title: "Active directory login and Gnome settings"
date: 2007-04-21
forum: Desktop Environments
---

### Post by Voland on 2007-04-21
I'm using Ubuntu Feisty as Active Directory domain member. I've configured authentication as it described [here]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto"). I can successfully log in this desktop, but trouble is DE settings. Domain user (domain admin) hasn't all possible menu items in System-Administrating section such local user  (first user) has. How can I get all rights for domain user?

---

### Post by s_p_a_r_k_y on 2007-04-21
might want to add this question over where more of the samba people are looking.

---

### Post by Voland on 2007-04-23
And where is this place on this forum? Could anybody help me?

---

### Post by Voland on 2007-04-24
I found partial solution of this problem: simply add domain user into /etc/group to groups where local user is a member. But I think it's not "ubunty way" - I can't add "Domain Admins" group. So problem is still unsloved.

---

