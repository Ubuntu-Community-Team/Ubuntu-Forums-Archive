---
title: "FTP download delay"
date: 2009-06-14
forum: General Help
---

### Post by [pl]ice on 2009-06-14
Hello,

 I'm looking for a software or a plugin for gftp. I'd like to do a download at nights etc (due to net restrictions) but i cannot find anything how to do it. Is there a simple way or do i have to write something and put it through cron? 
any ideas?

Thank you

---

### Post by andrew.46 on 2009-06-16
Hi [pl]ice,

> **'[pl]ice said:**
> I'm looking for a software or a plugin for gftp. I'd like to do a download at nights etc (due to net restrictions) but i cannot find anything how to do it. Is there a simple way or do i have to write something and put it through cron? 

I am not so sure about gftp but rather than use an elaborate script or cron etc I often simply use sleep and wget:

```
sleep 6h && wget *myfile.iso*
```

It is a little primitive but enables me to do some big downloading after midnight :-).

Andrew

---

### Post by [pl]ice on 2009-10-24
> **andrew.46 said:**
> Hi [pl]ice,



I am not so sure about gftp but rather than use an elaborate script or cron etc I often simply use sleep and wget:

```
sleep 6h && wget *myfile.iso*
```

It is a little primitive but enables me to do some big downloading after midnight :-).

Andrew

thnx :) will do for now!

---

