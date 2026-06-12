---
title: "How to optimise kernel for boot time?"
date: 2009-01-04
forum: General Help
---

### Post by blazemore on 2009-01-04
I'm getting a bit obsessive about shaving seconds off my boot time.
What, if any, options should I check/uncheck in xconfig, in order to get the fastest boot-time possible?
I have Core2 and need wireless.

---

### Post by oldos2er on 2009-01-04
> **blazemore said:**
> I'm getting a bit obsessive about shaving seconds off my boot time.
What, if any, options should I check/uncheck in xconfig, in order to get the fastest boot-time possible?
I have Core2 and need wireless.

 If you have a Core2Duo, you can enable CONCURRENCY=shell in /etc/init.d/rc.
Also disable any unneeded services (I like to use sysv-rc-conf for this).

---

### Post by zika on 2009-01-07
> **oldos2er said:**
> If you have a Core2Duo, you can enable CONCURRENCY=shell in /etc/sysctl.conf.
Also disable any unneeded services (I like to use sysv-rc-conf for this).
isn't the file that should be changed:**etc/init.d/rc** ?

---

### Post by oldos2er on 2009-01-07
> **zika said:**
> isn't the file that should be changed:**etc/init.d/rc** ?

 Yes, you're absolutely right. Thanks.

---

### Post by Idefix82 on 2009-01-07
> **oldos2er said:**
> If you have a Core2Duo, you can enable CONCURRENCY=shell in /etc/init.d/rc.


What does this option do?

---

### Post by bryncoles on 2009-01-07
> **Idefix82 said:**
> What does this option do?

as i understand it, concurrency=shell tells your computer to use both cores to load boot processes, instead of just the one. consequently, boot is mych faster. 

also, from grub, select the kernel you want to load and press 'e' to edit. pick the second line of the next screen (quiet splash i think) and press e to edit again. add the word 'profile' to the very end of this line and press return, then 'b' to boot. this boot will be very slow, as your computer will sift through what gets loaded in what order, and rearrange them for fastest future boots. 

do this after you have disabled unwanted startup services, or it'll be pointless!

---

