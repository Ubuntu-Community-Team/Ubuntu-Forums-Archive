---
title: "I instaled the ubuntu lamp server and..."
date: 2009-04-14
forum: General Help
---

### Post by horacle on 2009-04-14
I dont know how to work remotely with it; its a private server in a lan, we'll use it mainly to work with php, mysql, flash and html for testing before publishing work. All the development will be done remotely. Should I install ssh and/or ftp? samba? for editing we will be using from notepad to dreamweaver, to gedit, etc.

thanks in advance

---

### Post by 0cton on 2009-04-14
ssh is used for remote
ftp may be used to transfer files
but IIRC sftp is better sicne it aloows recursion copying
samba is for file sharing dont need it if you have ftp and ssh but you never know experiment

---

### Post by cariboo on 2009-04-14
Install openssh-server, and then use a combination of nautilus and sftp to manage files.

Jim

---

