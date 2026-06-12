---
title: "Print Accounting Software for cups"
date: 2009-03-17
forum: General Help
---

### Post by garethclark on 2009-03-17
I am trying to find some print accounting software for Ubuntu. I want to manage the jobs and add a user page limit to print jobs.

In the cups forum i was reccommended tea4cups or pykota but you have to pay for them.

What i really want to do is block all print jobs from the internet. But i am not sure if this is possible.

I was looking at editing the MIME database in cups to remove the conversion for those file types, but the guys at cups don't think this would work.

Any ideas guys?

---

### Post by garethclark on 2009-03-19
Ok found how to set quotas. In /etc/cups/printers.conf.

Thats fine. Still wondering if there is a way or program to block specific print jobs?

Like print jobs from the internet as previously mentioned.

---

### Post by garethclark on 2009-03-19
Just so you know.

I am administrating a network. We are running 8.04 server with LDAP authentication, but cups for printing.

All the clients are on 8.04 too.

---

