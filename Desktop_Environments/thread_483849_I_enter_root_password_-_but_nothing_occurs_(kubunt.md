---
title: "I enter root password - but nothing occurs (kubuntu)"
date: 2007-06-25
forum: Desktop Environments
---

### Post by kiev on 2007-06-25
All programs demanding root priveleges - do not react in any way to input root password - after input of the password the window of input is closed also anything. 
password correct
through the sudo (console) all works
please help

---

### Post by r0ck80y on 2007-06-25
Those applications need your normal user password since you, as that user, have the admin rights. Dont enter root password. Read more about the "sudo" system and you'll know

---

### Post by kiev on 2007-06-25
Yes, correctly, - user password 
sudo - works 
graphic mode - does not work

---

### Post by kiev on 2007-06-25
sudo tail -n200 /var/log/auth.log :

Jun 25 13:03:07  sudo: (pam_unix) auth could not identify password for [med63]
Jun 25 13:03:07  sudo: med63 : pam_authenticate: Conversation error ; TTY=pts/2 ; PWD=/home/med63 ; USER=root ; COMMAND=/usr/bin/kdesu_stub -

password for med63 correct

---

