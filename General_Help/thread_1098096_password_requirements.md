---
title: "password requirements"
date: 2009-03-16
forum: General Help
---

### Post by mariondeleeuw on 2009-03-16
Hello,

I installed Obuntu last week. Now I tried to login but I don't seem to use the right password. I think it is because of the fact that my usual password did not meet the requirements of an Obuntu password so I changed something in it. Can anybody tell me what they are, I think that when I know I remember what I changed.

---

### Post by taurus on 2009-03-16
Boot into recovery mode from GRUB menu.  Then, go into root shell and change the password for your account.  Assuming your login name is marion, do

```
passwd marion
```
Exit the session and reboot.  Now, can you login with marion (or whatever your login name) with that new password?

---

### Post by mariondeleeuw on 2009-03-16
Being a newbe I think I do something wrong. I rebooted in recovery mode then chose the schell. I typed pwd marion. I typed exit and booted. Then username: marion, password: marion'
But I did not succeed to login. So maybe I must have chose another username. But I can't imagine that. So what is possible now?

---

### Post by estyles on 2009-03-16
> **mariondeleeuw said:**
> Being a newbe I think I do something wrong. I rebooted in recovery mode then chose the schell. I typed pwd marion. I typed exit and booted. Then username: marion, password: marion'
But I did not succeed to login. So maybe I must have chose another username. But I can't imagine that. So what is possible now?

pwd = "print working directory", that's not going to help you.

You need to do passwd marion

---

### Post by mariondeleeuw on 2009-03-16
thanks, I am there. I seem to suffer from bad memory too.](*,)

---

### Post by sgosnell on 2009-03-16
It doesn't matter what Ubuntu says, you can use any password you want.  It may warn you that you're using a weak password, but that's all it will do.  Just click on Continue and don't worry about it.  There are no requirements, just the initial suggestion.

---

