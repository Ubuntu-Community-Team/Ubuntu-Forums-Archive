---
title: "problem to Start matlab"
date: 2008-05-29
forum: Education &amp; Science
---

### Post by Togras on 2008-05-29
when i try to start matlab license manager with
./lmstart

i get in the log file 2 errors:
**(lmgrd) Can't open /usr/tmp/.flexlm/lmgrdl.13510, errno: 13**
when i try to start matlab itself i get additional following message in the log file: **TCP_NODELAY NOT enabled ** :(

thx for your help and sorry for my bad English

---

### Post by thisismalhotra on 2008-05-30
> **Togras said:**
> when i try to start matlab license manager with
./lmstart

i get in the log file 2 errors:
**(lmgrd) Can't open /usr/tmp/.flexlm/lmgrdl.13510, errno: 13**
when i try to start matlab itself i get additional following message in the log file: **TCP_NODELAY NOT enabled ** :(

thx for your help and sorry for my bad English

try becoming  SUPERUSER by sudo or su and see if that works !!

---

### Post by Togras on 2008-05-31
> **thisismalhotra said:**
> try becoming  SUPERUSER by sudo or su and see if that works !!

no if do it with sudo i've to give the option -u and give a non superuser user -.- i'll tried it with sudo(and this option(without i get the message that i am not allowed to excute this as superuser)) as well, this leads to the same output in my logfile :(

thx for your help and sorry for my bad English

P.S i try it on different machines of friends today the outcome:
kubuntu same error as ubuntu
fedora crasy error message(some data missing on cd)
gentoo no error message but the installer doesn't start 
this programm drives me crasy -.-

---

