---
title: "Schedule a reboot?"
date: 2005-07-11
forum: Desktop Environments
---

### Post by gogo242 on 2005-07-11
How can I go about scheduling a weekly reboot on my machine?  I've googled it and read cron man pages....but they are greek to me!   ](*,)

---

### Post by mrcbrown on 2005-07-11
[QUOTE=gogo242]How can I go about scheduling a weekly reboot on my machine?  I've googled it and read cron man pages....but they are greek to me!   ](*,)[/QUOTE]
 could write a bash script to do: "shutdown -r now" in /etc/cron.weekly - why do you need a weekly reboot anyhow? Most linux systems run months, heck I have a few @ years at a time without a reboot.

---

### Post by jimbz on 2005-07-11
Hi

You have to add a line in /etc/crontab.

The fields are described by comments (you may also try 'man /etc/crontab' )but here is an example:

```
30 12 * * 2 root reboot
```

That will reboot your computer every tuesday at 12:30.

Let's explain that:

First: 5 fields to describe when cron will launch the command, they represent in order:
minutes(00-60)
hours(00-23)
day(1-31)
month(1-12 or jan, feb..)
day of the week(0-7 or mon, tue...)

Then the user who will launch the command

And the command (reboot in this case)

I hope this will help

Jim

---

### Post by IchBin on 2005-07-11
Correct me if I'm wrong but wouldn't the command be 'shutdown -r now' and not 'reboot' ???
I haven't tried reboot on ubuntu but I don't recall reboot ever working for me before. :)

---

### Post by az on 2005-07-11
Good question: why do you need to reboot?

---

