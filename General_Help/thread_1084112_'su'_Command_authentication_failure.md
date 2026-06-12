---
title: "'su' Command authentication failure"
date: 2009-03-01
forum: General Help
---

### Post by Scootymad on 2009-03-01
When i enter the 'su' command in the terminal it asks for a password, which i assume is my administrator password, but when i enter it i keep getting an authentication error.

Help?

---

### Post by Old *ix Geek on 2009-03-01
su requires the root password; sudo requires your password.

---

### Post by Scootymad on 2009-03-01
How would i know what the root password is?

---

### Post by fragos on 2009-03-01
There is no root password set in Ubuntu. Use sudo with your password. As a member of the admin group you're allowed to use sudo.

---

### Post by Scootymad on 2009-03-01
Im trying to do the following and its asking me for the password on the su command

[http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)

---

### Post by Xiong Chiamiov on 2009-03-01
In general, it's better practice to prefix commands that need root access with 'sudo'.  If you really need a root shell, however, you can replace su with 'sudo -s' or 'sudo -i'.

---

