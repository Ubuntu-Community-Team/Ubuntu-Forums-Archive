---
title: "su/do password?"
date: 2006-01-02
forum: Desktop Environments
---

### Post by welshgasman on 2006-01-02
Hi,

I'm using the Live CD version of Ubuntu on my laptop.

A LOT of what I am trying out requires sudo.

Is there a pw for su/sudo that I can use to start a session to carry out the commands.?

I've tried things like ubuntu and no password to no success.

TIA

---

### Post by tsunami on 2006-01-02
Apparently, no root password is set when installing Ubuntu. You can set a root password by issuing command $sudo passwd root
After that you can use root to log into the system

Cheers

---

### Post by giftnudel on 2006-01-02
There is no need to set a root password:
```
$sudo su -
```
should give you a root shell.
giftnudel

---

### Post by harisund on 2006-01-02
[QUOTE=welshgasman]
Is there a pw for su/sudo that I can use to start a session to carry out the commands.?
[/QUOTE]

Either you create a whole new account for root, or you simply open a new console dedicated to root, and do sudo -s. Then you will be logged in as root, without the need to actually create the root user.

---

### Post by welshgasman on 2006-01-02
>>$sudo su -

Worked a treat. Thank you

---

