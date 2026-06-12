---
title: "Help creating local network"
date: 2006-08-23
forum: Desktop Environments
---

### Post by marcostt on 2006-08-23
I want to create a local network between two computers that are connecting to internet trought a wifi router, both with kubuntu dapper. What must exactly I do? I choose the files to share in control panel, but i dont know how to find theses files since one of the computers to the other... and I want to share as well the printer of one of the computers.

---

### Post by VirtuAlex on 2006-08-23
you need to install samba and add samba users
sudo apt-get install samba
sudo smbpasswd -a username

---

### Post by marcostt on 2006-08-23
Ok, done, and now?

I have installed samba in both computers, but I dont now what must I do now to can accede from a computer to the other, or print since portatil computer in printer installed in the other computer.

---

### Post by VirtuAlex on 2006-08-23
as soon as you have created matching users it should be enough to start browsing the shares and as far as I know printers are shared by default

---

### Post by marcostt on 2006-08-24
Something does not work... since desktop computer I can accede tp portatil computer, but not the other way around: since portatil, clicking on Samba shared>MSWORKGROUP i can see the portatil (the name is "Portatil (Samba 3.0.22) ), but not the desktop computer.

---

### Post by VirtuAlex on 2006-08-24
I am not sure what are you talking about... You supposed to go through Places>Network Servers and open Windows Network browser.

---

