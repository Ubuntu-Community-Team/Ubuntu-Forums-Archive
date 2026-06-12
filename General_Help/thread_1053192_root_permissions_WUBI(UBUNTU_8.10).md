---
title: "root permissions WUBI(UBUNTU 8.10)"
date: 2009-01-28
forum: General Help
---

### Post by bovcan on 2009-01-28
First time I am using wubi and I download it and when I choose 
username and password I choose one x username.
But then I do not have any folder permition in OS.
OR how to log in as a root?

---

### Post by brandon88tube on 2009-01-29
Can you explain a little better? What folders do you not have permission to? Also, have you tried using sudo?

---

### Post by bovcan on 2009-01-29
I had problems in VAR/WWW folder(Desktop Edition)
but already solved the problem.

Loged in as a user, not root
alt + f2  then sudo nautilus
go into directory and edit file etc/gdm/gdm.conf
AllowRoot= false to AllowRoot =true

Then the root password id the same as password of a username witch I created on onstallation.

---

