---
title: "another vpn connection problem :P soz"
date: 2005-11-29
forum: Desktop Environments
---

### Post by trandojedi on 2005-11-29
ok... i've been at this for a while. and if i get this working, i'll beable to get rid of my slight dependence on windows (for this reason)... i'm at UWA in perth, western Australia, so if someone goes there, u will know about our SNAP vpn... well if u don't it's just a vpn that i can't connect to in linux :'(

the settings are here[http://www.ucs.uwa.edu.au/web/student/access/oncampus/snap/settings]("http://www.ucs.uwa.edu.au/web/student/access/oncampus/snap/settings")
some information resrouces are also here (go down till get to linux)
[http://www.ucs.uwa.edu.au/web/student/access/oncampus/snap/setup]("http://www.ucs.uwa.edu.au/web/student/access/oncampus/snap/setup")

anyways i got pptpconfig, and it running.

when i put in the information i get these errors...



Using interface ppp0pptpconfig: monitoring interface ppp0

Connect: ppp0 <--> /dev/pts/1
anon warn[pppt_gre_bind:ppptp_gre.c:95]: connect: Network is unreachable
anan fatal[main:pptp.c:251]:  Cannot bind gre socket, aborting.
Modem hangup
Connection terminated.
pptpconfig: pppd process terminated by signal 16 (failed)
pptpconfig: SIGUSR1



i'm thinknig that the program can't find my erthenet card or something like that... on my network in the top right of the screen it says it's connected and it says that using eth0

pls if anyone can help... help :D... cheers garrick

---

### Post by andho on 2006-07-20
hi
ive just started using linux and im trying to connecting to my broadband service provider vpn.
i ran into that same problem. it happens when i try to connect in a normal user. when i connect in root it works perfectly.

---

