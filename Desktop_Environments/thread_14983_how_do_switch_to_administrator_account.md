---
title: "how do switch to administrator account"
date: 2005-02-11
forum: Desktop Environments
---

### Post by gmike on 2005-02-11
i am sure this must have been answered somewhere else, please redirect me where to get that solution.

while installing ubuntu it said that administrator acount is disabled, that i have to create acount to be used, which i did but now i cannot do anything because i do not have right to do so.

everytime i am asked for root password and i typed password that was created with the name i use now it gives error message says that i do not have permission and passsword is not correct for root. due to this problem i cannot do anything with ubuntu. i want to change things so that i will have absolute right to do anything including breaking my system if i want to.

please help a complete newbie to ubuntu

---

### Post by lao_V on 2005-02-11
gmike,

You have to use sudo instead of su and use your normal user password

---

### Post by gmike on 2005-02-11
do i have do that each time i need to do something, installing stuffs and other thing thins?
anyway, thanks for you qucik reply

---

### Post by lao_V on 2005-02-11
[QUOTE=gmike]do i have do that each time i need to do something, installing stuffs and other thing thins?
anyway, thanks for you qucik reply[/QUOTE]
 Yes, just like you would use su, in Ubuntu you need to use sudo

---

### Post by ember on 2005-02-11
[QUOTE=gmike]do i have do that each time i need to do something, installing stuffs and other thing thins?
anyway, thanks for you qucik reply[/QUOTE]
 You may enable the root account by "sudo passwd root" and typing the new password.

If you want root to be able to login from gdm, you'll have to allow that in your system-settings.

---

### Post by az on 2005-02-11
"Yes, just like you would use su, in Ubuntu you need to use sudo"

Actually,

sudo su
to get to the root command line.

But there are lots of advantages in just using sudo.  It logs each command you do in /var/log/auto.log, for one.


Also, I do not think it is ever a good ides to run an X session as root.

---

