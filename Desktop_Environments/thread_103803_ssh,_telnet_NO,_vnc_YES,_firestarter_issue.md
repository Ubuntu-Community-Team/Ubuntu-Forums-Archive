---
title: "ssh, telnet NO, vnc YES, firestarter issue??"
date: 2005-12-14
forum: Desktop Environments
---

### Post by chopz on 2005-12-14
Hi all,
short-time lurker first time poster here :razz: 

I'm hoping SOMEONE here has had a similar issue and been able to fix it. I'm running firestarter on breezy and I"m trying to get my 2 ubuntu clients to talk to each other.  I firestarter shoudl be allowign traffic between the both of them with the rules i have in place.

1. On both ubuntu PCs ping to localhost works
2. VNC to the other ubuntu client on my network works
3. SSH and telnet from one pc to the other pc, or from one pc to itself does not work and does not even show up in firestarter's event log.  Error message i get from the command line with ssh is "connection refused port 22".  Similar error message for telnet
4. looking at /var/log/messages doesn't yield any corresponding error messages

I'm stumped. :confused:

---

### Post by cwaldbieser on 2005-12-14
[QUOTE=chopz]Hi all,
short-time lurker first time poster here :razz: 

I'm hoping SOMEONE here has had a similar issue and been able to fix it. I'm running firestarter on breezy and I"m trying to get my 2 ubuntu clients to talk to each other.  I firestarter shoudl be allowign traffic between the both of them with the rules i have in place.

1. On both ubuntu PCs ping to localhost works
2. VNC to the other ubuntu client on my network works
3. SSH and telnet from one pc to the other pc, or from one pc to itself does not work and does not even show up in firestarter's event log.  Error message i get from the command line with ssh is "connection refused port 22".  Similar error message for telnet
4. looking at /var/log/messages doesn't yield any corresponding error messages

I'm stumped. :confused:[/QUOTE]

Do you actually have sshd or telnetd running?

---

