---
title: "Need Sane Utilities"
date: 2009-01-15
forum: General Help
---

### Post by Indyviews on 2009-01-15
So close to getting a scanner going (I think) that is not supported. The latest hangup using the terminal is not being able to open or find Sane Utilities. So I put in a command to install them and now there is a locked file and it is asking if I am in root. I thought working the terminal was as if I were in root as to making changes...although this it didn't ask for my password. 

Does anyone know what I should do next..keep in mind I am in strange land here. Below is what I have at this time on the terminal:

steve@steve-desktop:~$ aptitude install sane-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
steve@steve-desktop:~$

---

### Post by wolfen69 on 2009-01-15
```
*sudo* aptitude install sane-utils
```
then you will be prompted to enter your password. password will not show on screen though.

just being in the terminal is not enough to be root. you must do sudo first. to work in the terminal as root so you don't have to enter sudo every time, type in ```
sudo su
``` then your whole terminal session will be as root.

---

### Post by Indyviews on 2009-01-15
Thanks **Wolfen69**...it appears I have a lot more installed, now if only   it gets me another step down the road...

---

