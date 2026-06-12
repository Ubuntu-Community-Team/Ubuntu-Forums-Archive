---
title: "Run commands as root at login"
date: 2009-03-16
forum: General Help
---

### Post by pelagic on 2009-03-16
Hello forum,

I have to run some commands at the login of a specific user as root (sudo).
How can I grant the right to run a specific command to a user without him having to enter his password? I want to include the command in his .profile.

Thanks for any hints!
/pelagic

---

### Post by nelskurian on 2009-03-16
You want to run a command at the bootup or run a specific command by your normal users without giving them sudo privilege and without giving th e sudo password.
I think the second one is correct.
So you can give the ACL permission to a specific user for a command by changing the ACL settings of command exicution file in /usr/sbin

---

