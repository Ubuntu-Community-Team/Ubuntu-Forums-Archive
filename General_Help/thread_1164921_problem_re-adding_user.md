---
title: "problem re-adding user"
date: 2009-05-20
forum: General Help
---

### Post by irvken on 2009-05-20
I added and then deleted a user from the command line and then maually added him to the the sudoers list. If I try to add a user in system > administration > users and groups it tells me the user already exists but he's not listed and if I try to delete him using the command line - sudo deluser hisname  its says no such user! what is going on?

---

### Post by _Purple_ on 2009-05-20
Go to System > Administration> Users and groups. Then click on unlock. After entering your password, click on manage group and make sure that the group with the same name as that particular user is deleted.

---

### Post by irvken on 2009-05-20
cheers I'll remember that

---

