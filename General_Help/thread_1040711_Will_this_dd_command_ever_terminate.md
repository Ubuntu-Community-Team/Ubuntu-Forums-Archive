---
title: "Will this dd command ever terminate?"
date: 2009-01-15
forum: General Help
---

### Post by ecolitan on 2009-01-15
I'm trying to zero a disk using dd for the first time, i ran # dd if=/dev/zero of=/dev/sda bs=1M 

It's been going for about an hour now and I was wondering if it will ever terminate? I don't want to stop it and have to do it again and wait another hour :P 

Cheers

---

### Post by Dave_Connor on 2009-01-15
With overwriting large amounts of data will take awhile so I would wait until the process is finished.

---

### Post by ecolitan on 2009-01-15
Cheers, i've decided that if it hasnt finished by the time I finish work i'll stop it anyway.

---

### Post by anjilslaire on 2009-01-15
I've dd'ed an 80gig drive & seen it take 4 hours on my laptop (1420 Inspiron)

---

### Post by pieisgood4589 on 2009-01-15
Yes, it does take a heckuva lot of time for the command to run and finish, just be patient.

---

### Post by cdtech on 2009-01-15
If you want to wipe a hard drive of all data (booting from a live cd of course) I'm sure that's what your doing:
```
dd if=/dev/zero of=/dev/sda conv=notrunc
```

---

### Post by HermanAB on 2009-01-15
Note that dd doesn't always terminate cleanly.  You can query it by sending it a signal using 'kill'.  

First you need to get its PID (open a second terminal!):
$ ps -e|grep dd

Then send it a signal:
$ sudo kill -USR1 PID

That will cause dd to hiccup and tell you how many bytes were copied.  If you do it multiple times and the number of bytes isn't changing, then you can safely stop dd with Ctrl-C.

Cheers,

Herman

---

