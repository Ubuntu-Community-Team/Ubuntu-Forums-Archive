---
title: "Pls help with wu-ftpd"
date: 2005-11-14
forum: Desktop Environments
---

### Post by QWERTY on 2005-11-14
I have installed wu-ftpd and added in inetd.conf:

ftp		stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/wu-ftpd -l -a -r /home/user/ftp

but I cannot connect:

ftp localhost
ftp: connect: Connection refused

What more do I need to make a an anonymous connection on my local network?

Thanks in advance.

---

### Post by Kyral on 2005-11-14
I think the problem is that you are trying to connect to yourself via the loopback address (127.0.0.1)

Also suggest this thread be moved to the Networking support forum

---

### Post by QWERTY on 2005-11-14
[QUOTE=Kyral]I think the problem is that you are trying to connect to yourself via the loopback address (127.0.0.1)[/QUOTE]

Tried to connect to the IP from another computer. The same.

[QUOTE=Kyral]Also suggest this thread be moved to the Networking support forum[/QUOTE]

Where can I find that? Not much help here, ha?

---

### Post by Kyral on 2005-11-14
Actually that second comment was more to the mods :P 

The Networking forum is here
[http://ubuntuforums.org/forumdisplay.php?f=101](http://ubuntuforums.org/forumdisplay.php?f=101)

---

### Post by QWERTY on 2005-11-15
Come on guys, someone must have used wu-ftpd!! :confused:

---

### Post by pabc on 2005-11-17
/bump.

Same problem here. I've installed from .deb and from source and in neither case can I start this service.

P

---

### Post by pabc on 2005-11-17
I got it working by adding wu-ftpd to sudoers as nopassword then adding

wu-ftp -Sa to the list of commands to run at startup in Sessions.

Without the -S it didnt work

P

---

### Post by QWERTY on 2005-11-19
[QUOTE=pabc]I got it working by adding wu-ftpd to sudoers as nopassword then adding

wu-ftp -Sa to the list of commands to run at startup in Sessions.

Without the -S it didnt work

P[/QUOTE]

Can you give me a more precise description of what yout did.

Thanx

---

### Post by xdefconx on 2008-01-03
> **QWERTY said:**
> Can you give me a more precise description of what yout did.

Thanx

HUhuhu me also looking for this solution huhuhuhu did anyone know how to solve it?

---

