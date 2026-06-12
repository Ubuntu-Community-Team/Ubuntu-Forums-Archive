---
title: "Launcher Problem"
date: 2005-03-24
forum: Desktop Environments
---

### Post by ohman11 on 2005-03-24
First of all I hope I am posting this in the right area. I created a launcher for gedit to open a file I use quite often and it works but it only lets me read the file. I need to set it up as root so I can edit it also. Here is the command I used.

"gedit /usr/share/qbrew/qbrewdata"  

Can someone tell me what I need to add to gain root privileges with this command line?

---

### Post by iomicifikko on 2005-03-24
sudo gedit ....

be careful


byez

---

### Post by ohman11 on 2005-03-24
[QUOTE=iomicifikko]sudo gedit ....

be careful


byez[/QUOTE]

Why do you say be careful.

---

### Post by Mr Black on 2005-03-24
I think they mean becarful when using the sudo or su commands because you have full access to the system.  So if you try to do something that might break, disable, the system in some way running as a normal user a lot of times your wouldn't have the rights to make those sort of changes.  But when running as the super user (su) the system just does what ever you ask it to.  So I guess they are trying to make the point that you should double check things when running them as root.

---

### Post by ohman11 on 2005-03-25
[QUOTE=Mr Black]I think they mean becarful when using the sudo or su commands because you have full access to the system.  So if you try to do something that might break, disable, the system in some way running as a normal user a lot of times your wouldn't have the rights to make those sort of changes.  But when running as the super user (su) the system just does what ever you ask it to.  So I guess they are trying to make the point that you should double check things when running them as root.[/QUOTE]


Got it..Thanks!

---

