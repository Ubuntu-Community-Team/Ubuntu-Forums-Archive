---
title: "Putty on Ubuntu"
date: 2007-10-29
forum: Desktop Environments
---

### Post by sacarrion on 2007-10-29
I've recently installed ubuntu (feisty fawn) on my laptop and installed putty through synaptic package manager and installed successfully but when I tried connecting to our server an error is popping "Unable to open connection to sshuser@host. Name or service not known"

Anybody encountered the same problem? How could I go by this problem? Is there any alternative to putty?

---

### Post by eldragon on 2007-10-29
putty is not needed since a ssh client is installed by default.
```
 $ ssh -p <port> user@host 
```

although, judging by the error message you had with putty, i bet you will get the same error with ssh ..
check if your server is not blocking connections from port 22, or if its behind a NAT, open port 22 to that server.

cheers

---

### Post by sacarrion on 2007-10-29
ssh is working fine with command line but I need putty to save the sessions and connection settings since I'm administering quite a number of servers and some  settings that I need to access regularly.

---

### Post by jachymc on 2007-10-29
Man, there is no alternative to putty in linux: Putty is the alternative to ssh on windows!

Man ssh, and see debian-administration for password-less login ([http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)).

---

### Post by wigg on 2007-10-29
You could make quick shell scripts, which would have all your settings in them.

---

### Post by airtonix on 2007-10-29
zenity would also help you gui'fy your scripts easily.

---

