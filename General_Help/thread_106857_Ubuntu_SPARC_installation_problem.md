---
title: "Ubuntu SPARC installation problem"
date: 2005-12-21
forum: General Help
---

### Post by kasl33 on 2005-12-21
I am having a heck of a time trying to install Ubuntu on my Sun Ultra 5 Sparc machine.  Here is what I have done so far - followed by my problems:

I installed the base system from the mini.iso and all was well.  After that, the system did the normal reboot that x86 users see and then it went to install the packages.  This failed because the /etc/init.d/interfaces file lacked the 'auto eth0' line.  After I fixed that and got the network running, I tried the sudo apt-get install ubuntu-desktop or apt-get aptitude install ubuntu-desktop and neither worked (using the sparc.ubuntu.org/ubuntu-sparc mirror.

Has anyone else had this problem?  Do you have a fix?

Lucky I can install some stuff like the SSH server and Apache - which is probably fine since this is only going to run as a server anyway, but it sure is nice to have a GUI sometimes :D

---

### Post by kasl33 on 2005-12-21
Ahh... never mind.  I just figured out that I was using the wrong mirror.  I had originally installed from a UK mirror which apparently has a different version of Ubuntu Sparc.  I just moved the mirror back to ports.ubuntu.com/ubuntu-ports from sparc.ubuntu.com/ubuntu-sparc and it seems to be installing the ubuntu desktop :)

It is kind of neat installing the OS through SSH - makes it more fun to search the internet while I am waiting.

---

### Post by BathroomNinja on 2005-12-21
[QUOTE=kasl33]Ahh... never mind.  I just figured out that I was using the wrong mirror.  I had originally installed from a UK mirror which apparently has a different version of Ubuntu Sparc.  I just moved the mirror back to ports.ubuntu.com/ubuntu-ports from sparc.ubuntu.com/ubuntu-sparc and it seems to be installing the ubuntu desktop :)

It is kind of neat installing the OS through SSH - makes it more fun to search the internet while I am waiting.[/QUOTE]


Good, because I had no idea where to even start

---

