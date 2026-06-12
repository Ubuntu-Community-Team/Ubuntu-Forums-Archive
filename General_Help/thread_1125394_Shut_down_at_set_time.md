---
title: "Shut down at set time"
date: 2009-04-14
forum: General Help
---

### Post by tazd on 2009-04-14
Is there a way to set Ubuntu to go into sleep mode at a pre set time i.e. say at 3am?

It's probably really easy but i have just switched over for windows so still finding my feet here :)

 I am running the latest beta of 9 in 64 bit if that makes any difference but i bet it don't  :)

Many thanks in advance for any and all help.

---

### Post by askreet on 2009-04-14
The commandline function you're looking for is:
```
pmi action suspend
```

If you want to have it occur at a certain time, edit your user cron:
```
crontab -e
```

Add a line like:
```
# suspend at 3AM every day.
00 3 * * * pmi action suspend
```

- askreet

---

### Post by askreet on 2009-04-14
An important addition, if you happen to be up at 3AM, it'll still suspend. :)

---

### Post by r1ch on 2009-04-14
Hi there,

what I use every now and then is...

```
sudo shutdown -h 12:00
```

... and replace 12:00 with whatever time you want to shutdown at in 24 hour clock. I think as written this is 'one use only' but there may be some help in the man file... try...

```
man shutdown
```

... and it may give you a few more usefull options.


correction......
sorry, I didn't read carefully enough where you mentioned 'sleep mode', don't think this is what you want then.

---

### Post by tazd on 2009-04-15
Many thanks to you all :) now i can doze off and not worry about leaving the lappy running :)

---

