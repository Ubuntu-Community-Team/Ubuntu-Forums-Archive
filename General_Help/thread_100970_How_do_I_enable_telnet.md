---
title: "How do I enable telnet?"
date: 2005-12-08
forum: General Help
---

### Post by mr.dad on 2005-12-08
I have just loaded a PC with Linux 2.6.12-10-386, or rather the blue Kubuntu distribution. All went well. I am very impressed.  I now want to enable telneting to the box. From a cygwin window on my other PC, I get: 

$ telnet 192.168.1.102
Trying 192.168.1.102...
telnet: Unable to connect to remote host: Connection refused

I suspect in need to turn on telnetd and/or open port 23, but don't see the GUI way of doing that. Is there one? Or, do I need to edit files. If so, which ones?

Thanks in advance for any advice,  Dave

---

### Post by ltmon on 2005-12-08
EDIT:  Oops, my bad.  SSH is not enabled by default.  You should be able to get it running pretty easily with the instructions at: [http://kudos.berlios.de/kf/kf1.html#openssh-server](http://kudos.berlios.de/kf/kf1.html#openssh-server)

My original post below
--------------

It's more secure to use ssh.

First:

> sudo /etc/init.d/sshd start

to set it going and then from your other box:

> ssh <ipaddress>

To do this in the GUI, you need to start up the services manager (somewhere in kcontrol, I never use it and am not at my computer now), find the "sshd" service and set it running and also set it to run at boot.

L.

---

### Post by mr.dad on 2005-12-08
That worked great.  Thanks, Dave.

---

### Post by christodoulos77 on 2007-01-14
I have the same problem but I want to use telnet because I want to telnet with Windows to my server. How do i enable telnet on ubuntu?

---

