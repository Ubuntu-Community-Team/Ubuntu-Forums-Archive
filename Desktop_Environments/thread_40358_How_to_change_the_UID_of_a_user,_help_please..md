---
title: "How to change the UID of a user, help please."
date: 2005-06-08
forum: Desktop Environments
---

### Post by skela on 2005-06-08
I was wondering how to change the UID of a user, without creating a new one. In the group/user window I cannot change the number of my user. Anyone?

---

### Post by skoal on 2005-06-08
sudo usermod -u <UID> <username>

* type "man usermod" for more options if you need 'em.

\\//_

---

### Post by skela on 2005-06-08
Thx!

---

### Post by stubby on 2005-06-08
[QUOTE=skela]Thx![/QUOTE]
 This isn't the section to ask for help

---

### Post by RastaMahata on 2005-06-12
admins, please move this :(

---

### Post by nocturn on 2005-06-13
[QUOTE=skela]Thx![/QUOTE]

Keep in mind when you do this that the files of that user will be owned by the previous UID.

To fix this:
find / -uid <olduid> -exec chown <newuid> "{}" ";"

---

