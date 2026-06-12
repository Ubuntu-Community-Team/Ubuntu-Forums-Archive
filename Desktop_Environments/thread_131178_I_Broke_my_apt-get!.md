---
title: "I Broke my apt-get!"
date: 2006-02-15
forum: Desktop Environments
---

### Post by QwizzTest on 2006-02-15
Hi,

I am kinda new to Linux.  I am going to put up a screenshot of what happens when I run apt-get with any command. (install, update, etc).  Sorry for the attachment as opposed to copy & paste.  I only have ssh access to the box right now so I justed used printscreen.

---

### Post by linkunderscore on 2006-02-15
does the box have internet connectivity?

---

### Post by aysiu on 2006-02-15
Either your sources.list is bad (sometimes the us.archive mirrors are no good, and I noticed some other weird Debian repository in there) or you don't have an internet connection.

If it's the former, see the first link of my signature.

---

### Post by penguain on 2006-02-15
that would be my guess

---

### Post by QwizzTest on 2006-02-15
[QUOTE=aysiu]Either your sources.list is bad (sometimes the us.archive mirrors are no good, and I noticed some other weird Debian repository in there) or you don't have an internet connection.

If it's the former, see the first link of my signature.[/QUOTE]
Okay, I'll check the sources.list file.  I'm using ssh to connect to it from across the city so I know the internet connection is there.  Also, firefox wasn't able to resolve host names.... but nslookup could from the command line.

---

### Post by QwizzTest on 2006-02-15
[QUOTE=linkunderscore]does the box have internet connectivity?[/QUOTE]
yes.

---

### Post by udha on 2006-02-16
[QUOTE=QwizzTest]Okay, I'll check the sources.list file.  I'm using ssh to connect to it from across the city so I know the internet connection is there.  Also, firefox wasn't able to resolve host names.... but nslookup could from the command line.[/QUOTE]
what about ping? It might just be the DNS on the machine is incorrect.

---

### Post by QwizzTest on 2006-02-16
[QUOTE=udha]what about ping? It might just be the DNS on the machine is incorrect.[/QUOTE]

Nope, I cannot ping 'wayne.edu', I get an unknown host error, however, I CAN ping the actual IP address of 'wayne.edu', which I can find using nslookup in the same ssh session.
What do I need to change?

---

### Post by QwizzTest on 2006-02-19
[QUOTE=QwizzTest]Nope, I cannot ping 'wayne.edu', I get an unknown host error, however, I CAN ping the actual IP address of 'wayne.edu', which I can find using nslookup in the same ssh session.
What do I need to change?[/QUOTE]



I figured out where the DNS problem was.  A program I was fooling around with (ultrapossum) changed my nsswitch.conf file so the it was looking to 127.0.0.1 instead of 'file' and 'dns'.

---

