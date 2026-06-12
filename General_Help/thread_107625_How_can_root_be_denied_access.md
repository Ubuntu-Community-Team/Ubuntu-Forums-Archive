---
title: "How can root be denied access?"
date: 2005-12-23
forum: General Help
---

### Post by funkadelic on 2005-12-23
If I am root, how can I be denied access? Case in point:

root@the-moose:/home/bozo/downloads/MPlayer-1.0pre7try2/MPlayer-1.0pre7try2/debian# ./config
bash: ./config: Permission denied

Please explain this to me -- I am new to Linux.

---

### Post by wylfing on 2005-12-23
1. You must have gone out of your way to become root in the first place. Stop it. There aren't any good reasons for being logged in as root. If you need to escalate your priveleges for a particular command, use sudo. For example, the command [FONT="Courier New"][COLOR="DimGray"]apt-get install samba[/COLOR][/FONT] requires elevated priveleges, so to run it you type:
```
sudo apt-get install samba
```

If you are asked for a password when you run commands with sudo, type your own user password. You do **not** need to be logged in a root, and in fact being logged in as root is extremely dangerous. Make sense?

2. Even root can be denied priveleges. The privelege system in Linux is comprised of three numbers, which represent priveleges to read, write to, and execute a particular file. Rather than get complicated about it, what you're experiencing in this instance is that the *execute* privelege is turned off. To turn it on do this:
```
sudo chmod +x ./config
```

---

