---
title: "created a launcher to reset network but..."
date: 2005-08-10
forum: Desktop Environments
---

### Post by ah.heng on 2005-08-10
i have to set it to open in terminal and manually enter the password.

is there a way to have the password included together with the command?

the command for the launcher is

```
sudo /etc/init.d/networking restart
```

---

### Post by Knome_fan on 2005-08-10
Did you try gksudo instead of plain sudo?
This should give you a graphical prompt for your password.

If you don't want to use a password at all, you could take a look at giving your user sudo right to execute this command without a password.

You can change the settings with sudo visudo and man visudo should give you an idea how the exact syntax should be. (Sorry, I don't mess around with sudo often enough to remember the exact syntax).

Hope this helps.

---

### Post by ah.heng on 2005-08-13
[QUOTE=Knome_fan]Did you try gksudo instead of plain sudo?
This should give you a graphical prompt for your password.

If you don't want to use a password at all, you could take a look at giving your user sudo right to execute this command without a password.

You can change the settings with sudo visudo and man visudo should give you an idea how the exact syntax should be. (Sorry, I don't mess around with sudo often enough to remember the exact syntax).

Hope this helps.[/QUOTE]
 i'll try it out. thanks.

---

