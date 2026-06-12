---
title: "[SOLVED] What's the root's password?"
date: 2008-12-12
forum: General Help
---

### Post by Bob John on 2008-12-12
I've just installed Ubuntu. During the time installing, I found the system didn't require me to set root password. Does the system have a default root password?

I also tried my own password for it,but it doesn't work.It means the root account does exist but its password I didn't know .

Will someone help me for this problem?
Thank you very much.

---

### Post by jpkotta on 2008-12-12
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ong on 2008-12-12
No. There is no default root password. in fact, the root account isn't enabled by default for security purposes. to enable it, go to users and groups and selects the root account property. then you can set your own root password.

---

### Post by lisati on 2008-12-12
Ubuntu is set up to use "sudo" to run commands that need root privileges, which uses the current user's password - the "root" account is often disabled for sercurity reasons.

---

### Post by MedianMajik on 2008-12-12
> **Ong said:**
> No. There is no default root password. in fact, the root account isn't enabled by default for security purposes. to enable it, go to users and groups and selects the root account property. then you can set your own root password.
  Be sure to learn about root before you mess with it!  It is deactivated for the user's protection.  Setting the password is fine, but it is wise to leave alone until you have a reason to use it.

---

