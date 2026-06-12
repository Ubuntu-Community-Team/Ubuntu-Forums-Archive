---
title: "dvd/ cd drive not detecting blank dvd"
date: 2009-03-29
forum: General Help
---

### Post by jkd18 on 2009-03-29
Pls help... not detecting blank dvd... Films play!

---

### Post by DeMus on 2009-03-29
> **jkd18 said:**
> Pls help... not detecting blank dvd... Films play!

What happens when you insert a blank disc? Does nautilus open automatically or does nothing happen?

---

### Post by jkd18 on 2009-03-29
totally nothing happens.. :(

---

### Post by rjl6591 on 2009-03-29
Try loading a blank DVD and then type this:

```
tail /var/log/kern.log
```

It should produce ten lines of output including something like this:

```
Mar 29 11:43:30 blahblah kernel: [160374.990104] cdrom: This disc doesn't have any tracks I recognize!
```

---

### Post by rjl6591 on 2009-03-29
Another thing worth checking is your file browser preferences.

Places -> Home Folder
Edit -> Preferences -> Media
Other Media -> Type: Blank DVD Disc

---

### Post by jkd18 on 2009-03-29
No what comes up is ":

Mar 29 16:40:43 jyothi-laptop kernel: [ 4229.487860]    groups: 03
Mar 29 16:41:00 jyothi-laptop kernel: [ 4237.228956] CPU0 attaching NULL sched-domain.
Mar 29 16:41:00 jyothi-laptop kernel: [ 4237.228965] CPU1 attaching NULL sched-domain.
Mar 29 16:41:00 jyothi-laptop kernel: [ 4237.240189] CPU0 attaching sched-domain:
Mar 29 16:41:00 jyothi-laptop kernel: [ 4237.240195]  domain 0: span 03
Mar 29 16:41:00 jyothi-laptop kernel: [ 4237.240199]   groups: 01 02
Mar 29 16:41:00 jyothi-laptop kernel: [ 4237.240202] CPU1 attaching sched-domain:
Mar 29 16:41:00 jyothi-laptop kernel: [ 4237.240204]  domain 0: span 03
Mar 29 16:41:00 jyothi-laptop kernel: [ 4237.240208]   groups: 02 01
Mar 29 16:41:11 jyothi-laptop kernel: [ 4242.139335] eth0: link up.


Even Gnomebaker - tho recognising drive is not recognising the DVDs...! :-(

---

### Post by rjl6591 on 2009-03-29
Sorry if this is a silly question, but are you trying to use a DVD-R disc in a DVD+R drive (or vice versa)?

---

### Post by jkd18 on 2009-03-29
I m trying to use a DVD+R 8.5 GB in a dvd+-RW

not hapng... :(

---

### Post by jkd18 on 2009-03-29
Ok, even when I change it to BLANK DVD disc in the preferences- media... it does not save the change and goes back to stooooopid Blu-rac setting....

---

