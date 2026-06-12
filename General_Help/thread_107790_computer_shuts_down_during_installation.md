---
title: "computer shuts down during installation"
date: 2005-12-23
forum: General Help
---

### Post by cker on 2005-12-23
Hi all - this is my first post in the forum - so hi to all and happy holidays

I am trying to install Ubunto 5.10 on my computer and am having some trouble.

the installation seems to go well but after I remove the CD and reboot and while the installation is installing the packages the computer shuts down (about 65% into the installation of the packages).

the message I have been getting is that there is a problem - either not enough space (I do not think this is the problem) a bug in the disc (again I do not think so because I tryed 2 different discs) or something else.

when I boot after this stage I am prompted to login with my user name and password and after I do that I receive something that looks like this:

[usr][host]@$#>:
what ever I type here I get the same response: bad command name or something to that extent.

Any ideas?

---

### Post by briancurtin on 2005-12-24
try "startx" in that prompt to start the X Window System

that will start up the GUI stuff and hopefully pick up where you left off in the installation process. im really not sure if that will do it, but its worth a shot and will get you to a better place than you currently are

---

### Post by cker on 2005-12-24
Thanks Brian

It did not work - I got the following message:

giving up.
xinit: Connection refused (errno 111): unable to connect to x server
xinit: No such process (errno 3): server error.

Any ideas?

Thanks Eyal

---

