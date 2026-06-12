---
title: "Remote printing not working"
date: 2005-12-21
forum: Desktop Environments
---

### Post by lduperval on 2005-12-21
HI,

I installed a new printer on my Breezy machine and it prints fine. Now, I want to be able to print remotely but my remote machine says it cannot access the CUPS server. I tried reaching port 631 on the remote machine (the Breezy machin) but I am unable to.

What is the problem? Is the port blocked? How do I unblock it?

Thanks,

L

---

### Post by manicka on 2005-12-21
Do you have a firewall such as Firestarter installed?

---

### Post by lduperval on 2005-12-21
I don' t see anything. Where would this be configured?

L

---

### Post by manicka on 2005-12-21
[QUOTE=lduperval]I don' t see anything. Where would this be configured?

L[/QUOTE]

If you've got it installed you will see it in 

Applications-->System Tools -->Firestarter

---

### Post by lduperval on 2005-12-21
I didn't have it installed so I installed it and it showed me that connections to port 631 were being blocked. I added a plicy to allow connections from my client to the remote server but it is still being blocked. I don't understand why.

Could it have anything to do with that IP6/IP4 thing?

L

---

### Post by lduperval on 2005-12-21
I also modified the /etc/cups/cupsd.conf file to accept connections from my host. I restarted CUPS, still no dice. :-(

L

---

### Post by manicka on 2005-12-22
Installing Firestarter won't solve the problem, I just wondered if you had one installed. How are you trying to share the printer? Is it to a windows or linux box?

This link may help
[https://wiki.ubuntu.com/NetworkPrintingFromWinXP](https://wiki.ubuntu.com/NetworkPrintingFromWinXP)

---

### Post by lduperval on 2005-12-22
I am trying to print from a Gentoo laptop. I can ssh correctly from my laptop to the Breezy server. I can telnet to port 631 on the Breezy machine, if I am logged onto the Breezy machine. But I can't telnet to port 631 from the Gentoo machine to the Breezy machine.

Hmmm... even though I am trying to connect to port 631 on the breezy machine, Firestarter doesn't report any activity on that port. I'm beginning to wonder if it isn't my laptop that isn't letting me access that port remotely.

Hmmm...

L

---

### Post by lduperval on 2005-12-22
Yes! It worked! The problem was with the Listen conficuration. It said 127.0.0.1 and I replacet it with Port 631 and now it works!

Thanks!

---

