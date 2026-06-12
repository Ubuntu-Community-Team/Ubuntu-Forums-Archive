---
title: "Network Interfaces"
date: 2005-12-18
forum: General Help
---

### Post by Thunk on 2005-12-18
When Ubuntu boots and runs all the tests, it stalls for over a minute in "configuring network interfaces".

Is that normal or should the whole process be quicker?

I'm using a DSL router to connect to the internet. Do I have somthing not configured properly?

---

### Post by kosmic on 2005-12-18
After you login to gnome can you browse the internet ?
 
go to a terminal and type : ifconfig
 
Is your router given ip adress ? (using DHCP) ? or did you put a static ip ?

---

### Post by Thunk on 2005-12-18
I can browse the internet. In fact, I am using Ubuntu to write this.
I am using DHCP and not a static IP.
ifconfig lists configurations for eth0, lo and ppp0.

Thanks!

---

### Post by alamba on 2005-12-18
Your system is basically looking out for an IP at that point in time. Maybe (i'm not sure) it takes time to build up the ppp0 interface.

Akshay

---

### Post by kosmic on 2005-12-18
TRy to give eth0 a static ip a see if it is faster.

---

### Post by Thunk on 2005-12-18
Worked great, thanks!

I can't believe it was that simple, I haveb't tried it because I couldn't belive that was the problem.

I guess I needed someone else to tell me to try that.

:D 

Thanks!

---

