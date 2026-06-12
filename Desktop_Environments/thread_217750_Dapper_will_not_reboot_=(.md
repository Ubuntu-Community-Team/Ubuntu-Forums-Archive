---
title: "Dapper will not reboot =("
date: 2006-07-17
forum: Desktop Environments
---

### Post by nr5 on 2006-07-17
Hello,

Just installed Dapper. 

When i try to reboot the system it stops at last message on the screen "Will now reboot" and the screen flashes every 5 or 10 seconds but it never reboots....

Shuting down the system is no problem, its the reboot that never reboots...

Pls help!

---

### Post by nr5 on 2006-07-18
Anyone?

---

### Post by squee on 2006-07-18
> **nr5 said:**
> Anyone?
I have a similar problem but I cant shut down. I tried deleting "splash" from

sudo gedit /boot/grub/menu.lst

that worked this morning but now I've updated and its not working so back to square one. My thread is  [http://www.ubuntuforums.org/showthread.php?p=1260722#post1260722](http://www.ubuntuforums.org/showthread.php?p=1260722#post1260722)

I hope this helps you.

---

### Post by utnubu001 on 2006-07-18
well it not like its a hectic problem..

---

### Post by TheMindField on 2006-07-18
This could be a kernel problem.

Boot into safe mode, and if you have internet, do:

"sudo aptitude update"

or if you want

"sudo apt-get update"

See if this helps.

---

### Post by squee on 2006-07-18
> **utnubu001 said:**
> well it not like its a hectic problem..
I love your comment!!!

I know its not that desperate to be solved but if I was happy settling for less, I'd have stayed with Windows.

---

### Post by palsyboy on 2006-07-19
I'm no expert, but you might try booting into Recovery Mode using the K/Ubuntu Alternate Install CD (the GUI live CD might have one, but I've never used it).  From there, you can become root and edit /boot/grub/menu.lst as per squee's instructions.  However, you'll probably want to run
```
#nano -w /boot/grub/menu.lst
```
or
```
#vi /boot/grub/menu.list
```
Or you could try to boot into Recovery Mode the same way but run
```
#apt-get update
#apt-get upgrade
```
as per TheMindField's instructions.

Good luck!

---

