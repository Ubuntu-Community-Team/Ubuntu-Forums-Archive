---
title: "help for basic stuff and acces denied"
date: 2009-01-23
forum: General Help
---

### Post by frostboy on 2009-01-23
hello. im new whit ubuntu.
1st: I would like to know how to have the permission to modify menu.lst in the /boot/grub folder.(I have to add some stuff to make my touchpad work properly)(Im the administrator usualy)
2rd: I would like to know were i can find good source for common stuff like accessibility manipulation, how to handle basic error and the basic think to know if I dont want to search 3 hour for every little issue I get.
thanks.

---

### Post by sisco311 on 2009-01-23
[list=1]
[*] Press Alt+F2 and run:
```
gksu gedit /boot/grub/menu.lst
```
The command opens the file in gedit (text editor) as root.

[uhelp]community/RootSudo[/uhelp]
[uhelp]community/FilePermissions[/uhelp]



[*] Community Documentation (link above).  

psychocats tutorials:[http://www.psychocats.net/ubuntu/permissions]("http://www.psychocats.net/ubuntu/permissions")
[/list]

---

### Post by drs305 on 2009-01-23
I recommend StartUp-Manager for newbies. It's a gui application that can edit the grub menu for you. You can set a variety of options that effect what you will see on grub's startup menu.

Here is a tutorial that describes how to install it and explains the various options:
[StartUp-Manager and Editing menu.lst]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by sisco311 on 2009-01-23
> **drs305 said:**
> I recommend StartUp-Manager for newbies. It's a gui application that can edit the grub menu for you. You can set a variety of options that effect what you will see on grub's startup menu.

Here is a tutorial that describes how to install it and explains the various options:
[StartUp-Manager and Editing menu.lst]("http://ubuntuforums.org/showthread.php?t=818177")

Thanks for the link. Very nice howto.

---

### Post by frostboy on 2009-01-30
Thanks all for the tips. its fine now.

---

