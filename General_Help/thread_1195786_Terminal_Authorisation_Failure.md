---
title: "Terminal Authorisation Failure"
date: 2009-06-24
forum: General Help
---

### Post by Alphalogan on 2009-06-24
As a novice with Ubuntu, when logging into Terminal and typing "su" I am asked for my password, I type in the password that I use to open Ubuntu but I get the message - "su: Authentication failure". What am I doing wrong?

---

### Post by lloyd_b on 2009-06-24
By default, Ubuntu does not have an active "root" account, which is what "su" is trying to switch to (root is disabled for security reasons).

Instead, Ubuntu uses the "sudo" mechanism.  "sudo <command>" will run <command> with root permissions, and "sudo -i" will create a true root shell.

Lloyd B.

---

### Post by Cheesemill on 2009-06-24
su won't work in Ubuntu because the root account doesn't have a password associated with it. See the following link for more info:
 
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Alphalogan on 2009-06-25
Many thanks for the help

---

### Post by Divider on 2009-06-25
you can however specify a password using

```
sudo passwd root
```

---

### Post by mcduck on 2009-06-25
> **Divider said:**
> you can however specify a password using

```
...
```

This is not recommended, and forum policy forbids from giving instructions how to do it. (as everybody who really needs to enable root account also already knows how to do that, or is able to figure it out easily. For the rest, they don't need to enable root, and if they do it becomes really hard to support people on these forums)

---

