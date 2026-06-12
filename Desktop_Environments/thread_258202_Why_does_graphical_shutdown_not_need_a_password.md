---
title: "Why does graphical shutdown not need a password?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by bruenig on 2006-09-15
When I do System>Quit then select shutdown, it shuts down without prompting for a password. 

Yet when I try to shutdown in the terminal "shutdown -h now" it says I must be root and not until I "sudo shutdown -h now" will it allow it to shutdown 

How does the graphical shutdown not require a password?

---

### Post by xhie on 2006-09-15
You need to be root to shutdown the system, graphical shutdown already has that, thats why you need to run it with sudo.

---

### Post by ayoli on 2006-09-15
graphical shutdown is doe by gdm which has its own user and must have rights for do that.
if you want to be able to shutdown without password prompt from terminal, etdit your sudoers file:
```
export EDITOR=gedit && sudo visudo
```
and add this line (replace *username* with yours):
```
username localhost= NOPASSWD: /sbin/shutdown -h now
```

---

