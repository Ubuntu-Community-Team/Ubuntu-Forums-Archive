---
title: "Root login"
date: 2009-04-11
forum: General Help
---

### Post by kr.ramprakash on 2009-04-11
Whether ubuntu supports "root" login or not?
How can i shift to root in Terminal?

---

### Post by dandnsmith on 2009-04-11
I think sudo su would do it.

---

### Post by Berserker v7 on 2009-04-11
To get into root mode for individual commands, prepend them with sudo.

To get into root session, use one of the following commands
```
sudo -s
```
```
sudo -i
```
or ```
sudo bash
```

To enable root through "su", execute the command ```
sudo passwd root
``` and then use su.

EDIT: Of course, sudo for individual commands is the only recommended way among these.

---

### Post by fuser312 on 2009-04-11
sudo passwd root

then type the desired root password

now when you want to use your terminal as root type "su" enter

and then give your root password.  now you have become a root

---

### Post by coffeecat on 2009-04-11
> **kr.ramprakash said:**
> How can i shift to root in Terminal?

The other posters have covered it, but bookmark this link:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

It's the official Ubuntu documentation for the Ubuntu way of root access in the terminal.

> **kr.ramprakash said:**
> Whether ubuntu supports "root" login or not?

Disabled by default, for good reason. Be aware that root login is contrary to forum policy. Link:

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

And a third complementary link:

[http://ubuntuforums.org/showthread.php?t=870137](http://ubuntuforums.org/showthread.php?t=870137)

---

