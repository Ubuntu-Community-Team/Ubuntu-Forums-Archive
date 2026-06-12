---
title: "Need to change the username"
date: 2011-09-03
forum: Desktop Environments
---

### Post by Heeter on 2011-09-03
Hi all,

Need to change the username on this desktop. The name located at the top right of desktop.

How do I do this?

This is for Ubuntu 11.04 32bit with Unity desktop.

I keep trying:
```

sudo usermod -l newname currentname

```
but I get that the user is logged in error.

Thanks

Heeter

---

### Post by haqking on 2011-09-03
> **kartabosh said:**
> beware that if you change your user he will no longer be a sudoer, you will have to manually add him in sudoers and maybe other files too 

if you still want to go along what you need to do is make sure you have a root password
type "su root" in a terminal and if it accepts the passwords you input you're good to go
otherwise type "sudo passwd root" and set a password to root
once you can access your root account log off the unity session
at the log in screen press CTRL+ALT+F2 (or any other F that will take you to a tty) log in with root and try your command 
since the user is not logged in anymore you shouldn't be getting that message


enabling the root account is not supported here in general as there are other methods

see here [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

see sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

