---
title: "sudo - fails"
date: 2005-04-10
forum: Desktop Environments
---

### Post by goldchip on 2005-04-10
Hi guys, just installed kubuntu yesterday, and having a problem - I can't do anything! Every time I open something that requires root access, it asks me for the root password.(yes, I know it's supposed to be blank, but it won't take blank p/w!  Even "sudo apt-get install whatever-package"
I've had a look through the forums b4 asking, and I've set a root p/w using the grub method, I've checked the /etc/sudoers, and '%admin ALL=(ALL) ALL' is present, so is my name in vigr (admin:x:109:andy)

Anyone see something I'm not???

---

### Post by soul_rebel on 2005-04-10
use YOUR password.
bye

---

### Post by goldchip on 2005-04-10
Ahhh, easy when u know how!
I'll try tomorrow, when I take the laptop to work - need to charge it up now.

Thanks for the quick reply m8

---

### Post by soul_rebel on 2005-04-10
Would you call it security putting a default blank password for root? root's default  password is something impossible to enter, no combination will work. If you want to get rid of sudo you can use "sudo su -"  and you will be logged as root. Then if you like you can use passwd to re-enable root, but ubuntu is built around sudo.
 :-D

---

