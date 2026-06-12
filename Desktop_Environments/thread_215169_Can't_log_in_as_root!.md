---
title: "Can't log in as root!"
date: 2006-07-13
forum: Desktop Environments
---

### Post by spahn on 2006-07-13
i feel so dumb, why can't i log in as root?
i type:
```

su root

```
then i type the password that i gave it during install...
 am i missing something?

---

### Post by etank on 2006-07-13
The root account is disabled by default. Use: ```
sudo -i
```instead. You could do ```
sudo passwd root
```to set the root password which enables the account but that is not recommended. To do something with root access use sudo.

---

### Post by Ramses de Norre on 2006-07-13
```
sudo su root
sudo -i
sudo -s
```
There are many options to log in as root, I'd use one of this instead of enabling the root acount. (read man sudo for more info about the differences)

---

### Post by T700 on 2006-07-13
The safest, easiest, way to act as root in Ubuntu is to invoke sudo or gksudo as a preface to a command.  For example:

```
gksudo gedit
``` will open the editor Gedit with root rights.  Use sudo for non-graphical apps and gksudo for graphical ones.  If you're running KDE, it is sudo and kdesu, instead.

Paul

---

### Post by spahn on 2006-07-13
Thank you very much!

---

### Post by spahn on 2006-07-24
Alright- new issue:

i have some mounted drives with another computer in the network. 

Problem is that i only see some of the directories and files, but i don't have permission to write to them!

I have spent days trouble shooting this issue, and today i found that if i change to root:
```
sudo su -
```
i can create and modify files, but only via command prompt (where i am recognized as root)

They are mapped in **/etc/fstab** and the folders are in the **mnt** directory (except for one that i put in my home folder to test permissions issues)

Any ideas or suggestions???

---

