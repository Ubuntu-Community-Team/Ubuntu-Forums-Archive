---
title: "root password changed?!"
date: 2009-03-28
forum: General Help
---

### Post by Jameshardy88 on 2009-03-28
Hi my root password tis morning no longer works, it says i ave te wrong password, i avent made a typing error and i am the only person (A) that uses my computer and (B) that knew the password. Wats going on and how can i sort this problem out?

---

### Post by DeMus on 2009-03-28
> **Jameshardy88 said:**
> Hi my root password tis morning no longer works, it says i ave te wrong password, i avent made a typing error and i am the only person (A) that uses my computer and (B) that knew the password. Wats going on and how can i sort this problem out?

Not only your password is checked, it is checked against your username. The combination of the two have to be right. Are you absolutely sure you also typed your username correctly? People always concentrate on their password and sometimes forget about the username.

---

### Post by sisco311 on 2009-03-28
in ubuntu the root password is locked by default.

you should use sudo for commands that require root privileges.

when sudo asks for a password, it needs YOUR USER password.

did you enabled the root account?

---

### Post by Jameshardy88 on 2009-03-28
sorry guys i've realised that my "h" key is broken =(

---

### Post by sekinto on 2009-03-28
You can change your root password by doing this:
sudo passwd root
When it asks for your password give it your password.
When it asks for the new root password give it the password you want.

---

### Post by sisco311 on 2009-03-28
> **Jameshardy88 said:**
> sorry guys i've realised that my "h" key is broken =(


You can boot in recovery mode to change your password.
[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

EDIT: NO need to boot in recovery mode!!!
open a terminal and type:
```
passwd
```
When you are asked for your password, instead of "h" press Ctrl+Shift+u and then enter 68, the hexadecimal Unicode character code for "h". [noparse](Ctrl+Shift+u 68)[/noparse]

---

### Post by kdcoetzee on 2009-03-28
Or, use a livecd, boot up.

Mount the drive and edit your /etc/shadow file to remove root password.

---

