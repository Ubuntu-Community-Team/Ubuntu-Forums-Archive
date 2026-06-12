---
title: "Workaround for gksudo gnome-terminal"
date: 2009-06-29
forum: Desktop Environments
---

### Post by borokov on 2009-06-29
Hey,

Since gksudo gnome-terminal is broken in Ubuntu 9.04 Jaunty Jackalope, a workaround would be handy for those who use this tool often.
This could be fixed by running gnome-terminal -e "sudo -i", but that would still require you to enter a password.
Another solution is the following:

1) Install ssh server:
```
aptitude install openssh-server
```
2) Under your regular account:
```
ssh-keygen
```
3) From a regular login terminal:
```
ssh-copy-id root@localhost
```
4) Enter the root password when requested
5) /etc/ssh/ssh_config:
```

   Host localhost
   User root

```
6) Change the properties for the gnome-terminal desktop icon (right-click):
```
gnome-terminal -e "ssh localhost"
```

This way, whenever you click the terminal icon, you get a root ssh shell to your own system.

HTH,

Boro

---

