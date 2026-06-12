---
title: "Help Gaining Root Privileges"
date: 2008-12-25
forum: General Help
---

### Post by Isilion on 2008-12-25
hi, i would like to manipulate my computer from class. im using ubuntu 8.10 and in class i use windows vista and ubuntu. i dont know if using telnet is the good way, or if there is another better, can you help me? in short what im looking for is gaining root privileges in my computer from another, wherever i were. can anyone tell me plz?thanks.

---

### Post by jayk121121 on 2008-12-25
You can use [SSH]("http://suso.org/docs/shell/ssh.sdf") to access your computer remotely. There is a Windows SSH program called [PuTTY]("http://en.wikipedia.org/wiki/PuTTY"). In order to run a command as root, run sudo plus the command in a terminal. For example:
```
sudo apt-get install kubuntu-desktop
```

---

### Post by Isilion on 2008-12-25
thx. i tryed ssh.

i followed this tutorial to authenticate my conecction. 

[http://tuxpepino.wordpress.com/2007/05/11/ssh-el-dios-de-la-administracion-remota/](http://tuxpepino.wordpress.com/2007/05/11/ssh-el-dios-de-la-administracion-remota/)

i addded these lines to sshd_config:

MaxAuthTries 1
MaxStartups 1
AllowUsers username username@x.x.x.x (known ip)

 when i use:

# ssh -p 666 username@m.y.i.p

 i get this error:

ssh_exchange_identification: Connection closed by remote host

any help?

---

