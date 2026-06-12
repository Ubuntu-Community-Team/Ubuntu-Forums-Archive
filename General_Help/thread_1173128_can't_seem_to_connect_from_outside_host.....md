---
title: "can't seem to connect from outside host...."
date: 2009-05-29
forum: General Help
---

### Post by mikeymayhem on 2009-05-29
first, thanks for viewing my problem... my problem is this... 

i'm trying to setup a universal shell access that my friends can connect to so we can do some C++ development, the problem is that they can't always come to my house to do so sometimes they need to be at work and be able to connect to the shell from there computers at work... i've been attempting to localize the connection to outside users and set up there account but the problem is that when they connect they only get a openbsd debian banner and no login prompt.. this is my problem is there something im not doing to activate that prompt, can someone please help me ....

---

### Post by mikeymayhem on 2009-05-29
reposting for help

---

### Post by nebileix on 2009-05-29
Wat are u using for the remote shell? Openssh?

Did you do any port forwarding?

---

### Post by mikeymayhem on 2009-05-29
well it does connect via port 23 but all it displays is this:


mayhem@ubuntu:~$ telnet
telnet> open 192.168.2.4 23
Trying 192.168.2.4...
Connected to 192.168.2.4.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1



the problem is there is no login and password prompt

---

### Post by binary10 on 2009-05-29
> **mikeymayhem said:**
> well it does connect via port 23 but all it displays is this:


mayhem@ubuntu:~$ telnet
telnet> open 192.168.2.4 23
Trying 192.168.2.4...
Connected to 192.168.2.4.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1



the problem is there is no login and password prompt


You've got ssh'd sitting on port 23 - nothing wrong in that. Just make sure that you've got it secured enough to stop every man and his dog from attempting to get in (if connecting up to the inet).

Use ssh 192.168.2.4 -p 23 to logon..

---

### Post by nebileix on 2009-06-01
use ssh is safer.

---

