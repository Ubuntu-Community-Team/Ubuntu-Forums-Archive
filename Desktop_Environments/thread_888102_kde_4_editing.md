---
title: "kde 4 editing ??"
date: 2008-08-12
forum: Desktop Environments
---

### Post by rixtr66 on 2008-08-12
i just installed kubuntu 8.04.1 with kde4,and i discovered very quickly that kdesudo and kwrite dont work,i need to copy a portion of the/boot/grub/menu.lst,what do i use to edit?
rick

---

### Post by overdrank on 2008-08-12
Moved :)


Hi and it has been awhile since I have used KDE but have you tried kdesu kate

---

### Post by rixtr66 on 2008-08-12
this is what i get;
rick@kubuntu4:~$ kdesu kate /boot/grub/menu.lst
passprompt

sudo: kate: command not found

rick@kubuntu4:~$

---

### Post by overdrank on 2008-08-12
> **rixtr66 said:**
> this is what i get;
rick@kubuntu4:~$ kdesu kate /boot/grub/menu.lst
passprompt

sudo: kate: command not found

rick@kubuntu4:~$

Hi and have you tried installing kate or kwrite from adept manager.

---

### Post by sjhstorm on 2008-08-13
Hi

Unfortunately you have to use the path at the moment i.e

kdesu /usr/lib/kde4/bin/kate

this will start kate with root

Steve

---

