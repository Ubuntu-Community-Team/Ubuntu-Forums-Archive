---
title: "editing GRUB... error"
date: 2005-12-20
forum: General Help
---

### Post by ESPOiG on 2005-12-20
how do i edit the grub boot loader using the terminal

i found wat to type in on the forums but wen i try i get the error
"cp missing destination files" that is from sudo cp /boot/grub/menu.lst

and i dont wanna mess around with users just to login as the root to edit it... and i do have the root passwrd set it just wont let me edit through the terminal

any ideas??

---

### Post by aysiu on 2005-12-20
```
sudo cp /boot/grub/menu.lst **/boot/grub/menu.lst_backup**
``` The **bold** part is the "missing destination" referred to by the error.

---

### Post by invalid on 2005-12-20
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.orig
sudo nano /boot/grub/menu.lst
```

---

### Post by earobinson on 2005-12-20
[QUOTE=aysiu]```
sudo cp /boot/grub/menu.lst **/boot/grub/menu.lst_backup**
``` The **bold** part is the "missing destination" referred to by the error.[/QUOTE]
and then a ```
 sudo gedit /boot/grub/menu.lst
```

---

### Post by ESPOiG on 2005-12-20
[QUOTE=aysiu]```
sudo cp /boot/grub/menu.lst **/boot/grub/menu.lst_backup**
``` The **bold** part is the "missing destination" referred to by the error.[/QUOTE]

so now i have put it all in the whole thing... and no error occured... but nothin happend so what now :D

---

### Post by invalid on 2005-12-20
It should give you no output if the copy was successful. Now edit it using the commands above.

---

### Post by bonjun on 2005-12-20
> 
Quote:
Originally Posted by aysiu
Code:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

The bold part is the "missing destination" referred to by the error.

so now i have put it all in the whole thing... and no error occured... but nothin happend so what now 

nope, there is, you have created your menu.lst_backup, your backup of your **menu.lst**
you can check:
> ls /boot/grub/menu.lst_backup

now you can edit your menu.lst

Code:
> sudo nano /boot/grub/menu.lst

as **nano** is a text editor

---

### Post by ESPOiG on 2005-12-20
nup still not workin

this is wat i have done

sudo cp /boot/grub/menu.lst /boot/grub/menu_backup.lst

then

sudo cp /boot/grub/menu.lst - this comes with the error cp: missing destination file

and that nano thing confuses me more... im not a regular linux user :D anyhelp plz :D

---

### Post by invalid on 2005-12-20
You seem to be typing only half of the command. Type exactly:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu_backup.lst
```
and then
```
sudo gedit /boot/grub/menu.lst
```

Do a copy paste if you need to, you are leaving off part of it.

---

### Post by ESPOiG on 2005-12-20
k got it now... how do i get it to boot win xp as default...

---

### Post by invalid on 2005-12-20
Find the number that belongs to your XP partition, and use that in the line that says ```
default #
```

---

### Post by ESPOiG on 2005-12-20
well im stuffd... i used the cut and paste option from a link i found (apprentley workd) but wen i did it it faild and now i have 2 more options for boot liunx :D

---

### Post by chaumurky on 2005-12-20
You've messed something up. It's a good thing you have that copy. Restore to the original by going:

** sudo cp /boot/grub/menu.lst.backup /boot/grub/menu.lst**

now open it again:

** sudo gedit /boot/grub/menu.lst**

Find the line that says 

** default 0**

and change the **0** to a **4**.

Save it and see how you go.

---

