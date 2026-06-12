---
title: "boot change needed"
date: 2005-12-21
forum: Desktop Environments
---

### Post by tuxster on 2005-12-21
Hi all, I a ubuntu noobie and this is my first post.

A couple of questions:
I installed ubuntu on my IBM Thinkpad T20 laptop.  It installed with no problems but my thinkpad has a 3com mini pci 10/100 network card in it and the 3c linux driver for this card doesn't work with power management enabled.  I think I need to add something like acpi=off to the boot instructions, but where and how ?  There are no boot options under preferences or administration.  Can I add it to a file ?

Second question is, I don't remember being asked to enter a root password during setup, and I can"t "su" to root.  Did I just forget entering the password or can you not su to root with ubuntu ?

Thanks in advance

---

### Post by codejunkie on 2005-12-21
[QUOTE=tuxster]Hi all, I a ubuntu noobie and this is my first post.

A couple of questions:
I installed ubuntu on my IBM Thinkpad T20 laptop.  It installed with no problems but my thinkpad has a 3com mini pci 10/100 network card in it and the 3c linux driver for this card doesn't work with power management enabled.  I think I need to add something like acpi=off to the boot instructions, but where and how ?  There are no boot options under preferences or administration.  Can I add it to a file ?

Second question is, I don't remember being asked to enter a root password during setup, and I can"t "su" to root.  Did I just forget entering the password or can you not su to root with ubuntu ?

Thanks in advance[/QUOTE]
ubuntu uses sudo instead of su so to gain root access you use this command  
```
sudo su
```and enter your password 
for apps use gksudo, for example:
```
gksudo nautilus
``` opens nautilus with root permissions
and the file you need to add the boot parameter to is the /boot/grub/menu.lst
file.

---

### Post by Dr. Nick on 2005-12-21
1. The file you most likely need is /boot/grub/menu.list. Dont know how to add that line though, I used to do it with lilo but not grub

2.Su doesnt work by default, Ubuntu uses sudo. So to run a command as rood prefix it with sudo and then enter you password

Or do what codejunkie said lol

---

### Post by tuxster on 2005-12-21
OK Thanks Dr Nick and codejunkie.  I can sudo into root now and I can edit the boot menu.lst file now.

Mike

---

### Post by Kirt on 2005-12-25
[QUOTE=codejunkie]ubuntu uses sudo instead of su so to gain root access you use this command  
```
sudo su
```and enter your password 
for apps use gksudo, for example:
```
gksudo nautilus
``` opens nautilus with root permissions
and the file you need to add the boot parameter to is the /boot/grub/menu.lst
file.[/QUOTE]

Hi!

Still new to Linux :oops: - when you use examples to type into Kubuntu, do you mean in a terminal? Do I have to do this for everything I would want to , say, edit or change? (Great security feature, but a real pain to find info on! ;) )

---

### Post by Dr. Nick on 2005-12-25
[quote=Kirt]Hi!

Still new to Linux :oops: - when you use examples to type into Kubuntu, do you mean in a terminal? Do I have to do this for everything I would want to , say, edit or change? (Great security feature, but a real pain to find info on! ;) )[/quote]

Yeah those type of commands need to be in a terminal, or Konsole as I believe kde calls it,

You only need to use sudo to make changes to system files, It is sorta a security feature, but sudo usage should not really be required for day to day usage.

Some of the commands have a graphical equivelant, but that is not the same between kde and gnome plus the other desktops so alot of people refer to the command line since it is more standard across all enviroments

---

