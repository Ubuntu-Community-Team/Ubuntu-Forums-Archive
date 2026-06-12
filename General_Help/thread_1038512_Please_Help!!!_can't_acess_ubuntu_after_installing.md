---
title: "Please Help!!! can't acess ubuntu after installing windows 7"
date: 2009-01-12
forum: General Help
---

### Post by Hyper Tails on 2009-01-12
hi I quaterate booted my laptop with xp/vista/7 and ubuntu and I installed 7 last after ubuntu and now i can't get into ubuntu

Help Please!!!

---

### Post by daprofessor on 2009-01-12
should be able to fix it from a live CD, 

From Terminal

sudo grub
find /boot/grub/stage1
(Use the output from this command in the next command)
root (hd0,1)
setup (hd0)
quit

reboot and edit grub to list all of the window installs.

---

### Post by Hyper Tails on 2009-01-12
this sound kind of hard to do

anything else
or make this a bit easyer

---

### Post by daprofessor on 2009-01-12
It's should be easy...

1) Boot From Live CD
2) Open Terminal and type the following commands 
   sudo grub
   find /boot/grub/stage1   <----- Whatever this says use in parentheses 
   root (hd0,1)
   setup (hd0)
   quit

reboot

Just make sure before you do anything with computers to back up your data!!!

---

### Post by Dustin2128 on 2009-01-12
doesn't sound hopefull to me... I would've installed 7 in a virtual machine, but since your computer is messed up, it's probably a windows problem. Most likely with the boot manager. What happened is that it replaced GRUB with its own boot manager, which can't handle more than 3 OSes at a time. So obviously, it follows its programing and takes out the competition. reinstalling GRUB should do the trick.

---

### Post by Hyper Tails on 2009-01-13
How do I reinstall grub?

---

### Post by bodhi.zazen on 2009-01-13
> **Hyper Tails said:**
> How do I reinstall grub?

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by Hyper Tails on 2009-01-13
> **bodhi.zazen said:**
> [uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

Thank you so much!!!

Solved

---

