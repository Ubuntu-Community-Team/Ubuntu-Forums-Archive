---
title: "tty problem. locked out of system. urgent!"
date: 2009-04-01
forum: General Help
---

### Post by mrjohnsen on 2009-04-01
Hi
I'm having some problem with a Ubuntu 8.04 Server x64. It locks everyone out from the server with the login error: 

init: tty1 main process (4953) terminated with status 1
init: tty1 main process ended, respawning

Can't login at all. I have a feeling that it has something to do with that i moved /home from it's own partition to the / partition. 

[IMG]http://www.mrjohnsen.net/problem.jpg[/IMG] 

Any help is very appreciated.

---

### Post by albandy on 2009-04-01
it could be. 
Enable the root user and enter with it, as root uses /root and not /home 

Boot in rescue mode
select a root session
then type a password to root user: passwd root
exit and reboot

now login as root

---

### Post by mrjohnsen on 2009-04-01
Thanks for your fast reply! I tried to enable root but it gave the same error on login.

The only things that is done with the server is: moving /home as mentioned, installed vmware-tools, installed zimbra.

---

### Post by albandy on 2009-04-01
have you tried to login throught an ssh connection?

---

### Post by mrjohnsen on 2009-04-01
Yep, doesn't work.

---

### Post by albandy on 2009-04-01
and what's the error message when doing an ssh  connection?

---

