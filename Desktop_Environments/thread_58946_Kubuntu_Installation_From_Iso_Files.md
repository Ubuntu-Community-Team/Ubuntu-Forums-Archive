---
title: "Kubuntu Installation From Iso Files"
date: 2005-08-22
forum: Desktop Environments
---

### Post by sayyidhassan on 2005-08-22
I downloaded kubuntu-5.04-install-i386.iso from a WinXp machine and burnt it on a CD. When I tried to: 
sudo apt-get install kubuntu-desktop, 
I get a message saying the file cannot be found.
I need guide on how to install it on an Ubuntu machine.

Best regards,
Hassan

---

### Post by heimo on 2005-08-22
Just to make things a bit more clear. Is this the scenario? You have Ubuntu installed on one computer (apparently without network connection) and you want to intall Kubuntu (KDE) on it? You have Kubuntu CD.

Haven't done that, but I believe you'll have to add that CD to repositories using Synaptic (for example) and then update package database (refresh-button) and try again.

---

### Post by sayyidhassan on 2005-08-22
[QUOTE=heimo]Just to make things a bit more clear. Is this the scenario? You have Ubuntu installed on one computer (apparently without network connection) and you want to intall Kubuntu (KDE) on it? You have Kubuntu CD.

Haven't done that, but I believe you'll have to add that CD to repositories using Synaptic (for example) and then update package database (refresh-button) and try again.[/QUOTE]

you got the scenario right.how do i add the cd to repositories?

---

### Post by sayyidhassan on 2005-08-22
[QUOTE=sayyidhassan]you got the scenario right.how do i add the cd to repositories?[/QUOTE]
 you got the scenario right.how do i add the cd to repositories?

---

### Post by heimo on 2005-08-22
I believe there's option in the menus of Synaptic to do just that. It's not exactly same as adding online (ftp/http) repositories, but anyway, this may help a bit:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by SGC on 2005-08-22
From the terminal, run the following commands:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install kubuntu-desktop
```

---

### Post by sayyidhassan on 2005-08-23
thanx,i was successful

---

