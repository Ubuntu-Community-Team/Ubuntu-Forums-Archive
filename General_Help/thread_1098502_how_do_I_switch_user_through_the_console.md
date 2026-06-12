---
title: "how do I switch user through the console?"
date: 2009-03-17
forum: General Help
---

### Post by sa125 on 2009-03-17
Hi - I'd like to switch users in the console, and not necessarily go to root (which is sudo -i). Say go from user "dave" to user "john". I'm sure it's real simple, just couldn't find it :)

Thanks!

---

### Post by heindsight on 2009-03-17
You need to use su.

For example, if you're logged in as dave and you want to become john, do:
```
su -l john
```
and type john's password.

---

### Post by sa125 on 2009-03-17
Thanks!

---

### Post by sisco311 on 2009-03-17
EDIT:
if you have admin rights, you can use sudo:
```
sudo -i -u username
```
the password being asked for is your own.

---

