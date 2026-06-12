---
title: "Uptimed and dual booting"
date: 2009-06-15
forum: General Help
---

### Post by prominance on 2009-06-15
If anyone is well versed with uptime daemon (uptimed) this question is for you:  Is it possible to use configure uptimed to also monitor my Windows partition uptime (boot times, records, etc)?

I am dual booting Windows Vista and Ubuntu and uptimed is working perfectly for my Ubuntu partition, but I would like to extend it to keep track of my uptime when I'm using my Windows partition as well.

It may be that I would have to search for a Windows program / script that would record the same information as Ubuntu's boot logs and then dump them in my Ubuntu partition.

I thought I would see if anyone else knows of an easy way to do it.  Thanks for any help you can offer!

---

### Post by briguy47 on 2009-06-15
> **prominance said:**
> If anyone is well versed with uptime daemon (uptimed) this question is for you:  Is it possible to use configure uptimed to also monitor my Windows partition uptime (boot times, records, etc)?

I am dual booting Windows Vista and Ubuntu and uptimed is working perfectly for my Ubuntu partition, but I would like to extend it to keep track of my uptime when I'm using my Windows partition as well.

It may be that I would have to search for a Windows program / script that would record the same information as Ubuntu's boot logs and then dump them in my Ubuntu partition.

I thought I would see if anyone else knows of an easy way to do it.  Thanks for any help you can offer!


You can't use ubuntu's "uptime" command directly since only os would be running at any given time.

However in Windows, you can do this at the command prompt:

```
net stats srv
```It will say something like "Statistics since..."  that is the uptime.  :)


Let me know if you have any questions!  :D

---

