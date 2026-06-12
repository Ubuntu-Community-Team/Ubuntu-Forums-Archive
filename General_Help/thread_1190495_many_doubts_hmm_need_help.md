---
title: "many doubts hmm need help"
date: 2009-06-17
forum: General Help
---

### Post by chandu73 on 2009-06-17
Hi,
1) i want to set up tftp  server on ubuntu 8.04 . for that i did

$sudo apt-get install xinetd tftpd tftp.

and i tested for properly installed or not by giving the command 

$/usr/sbin/in.tftpd -V

but not getting any output, i dont know whether i insteld it properly r not.

2) how to list out the users in a particular group, and how to add a existing user to a particular group. because i need to access the ttyS0 terminal for serial i/o.

 $ ls -l /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 2009-06-18 17:56 /dev/ttyS0

for  this i need to add one existing use say user1 to dialout, how can i do it from CLI

Regards
chandu

---

### Post by jonobr on 2009-06-17
Hello

I dont want to steer you in another direction if your happy with the app your using,

however, I used tftp-hpa , installed it from synaptic modified the config, started the daemon and it worked fine.

Coould you give that a try and see if it works any better.?

---

### Post by jonobr on 2009-06-17
Heres the steps I used 

Install tftpd-hpa

apt-get install tftpd-hpa

2: Configure TFTP
 Edit "/etc/default/tftpd-hpa" to include: Set RUN_AS_DAEMON="yes"

Edit "/etc/default/tftpd-hpa" to include: OPTIONS="-l -v -s /tftpboot" 
This is where a machine gets its tftpboot info

---

