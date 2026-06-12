---
title: "Request Help!!!"
date: 2006-02-25
forum: Desktop Environments
---

### Post by naveents on 2006-02-25
I need to modify the menu.lst file in boot/grub... But that file is marked as read only!! I cannot change the settings!! I need to log in as root but i cannot find any root password!! There was no request to enter the root password while installing!! I am the only user in the system!! Plz help

---

### Post by soonindallas on 2006-02-25
use the command

```
sudo gedit /boot/grub/menu.lst
```

to use superuser priveliges to edit the file.

type your user password at the prompt.

---

### Post by naveents on 2006-02-25
[QUOTE=soonindallas]use the command

```
sudo gedit /boot/grub/menu.lst
```

to use superuser priveliges to edit the file.

type your user password at the prompt.[/QUOTE]
where d i type this???in terminal???

---

### Post by Ramses de Norre on 2006-02-25
Yes, you're correct saying you don't have a root password but that's normal in ubuntu.
All the root tasks can be done by the program sudo. When you type sudo in front of a command, you run it as root. And the password he asks is your normal user password.

---

### Post by soonindallas on 2006-02-25
[QUOTE=naveents]where d i type this???in terminal???[/QUOTE]

yep.  Applications>accessories>terminal

---

