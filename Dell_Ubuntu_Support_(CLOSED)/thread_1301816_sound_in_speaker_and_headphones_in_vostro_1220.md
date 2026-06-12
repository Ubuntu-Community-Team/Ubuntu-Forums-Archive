---
title: "sound in speaker and headphones in vostro 1220"
date: 2009-10-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nu_kru on 2009-10-26
Hi, 

I have a dell vostro 1220 with a HDAudio Controller (ubuntu, 9.10, 64b):

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

 The audio plug which doesn't seem to turn off the **speaker** when headphones are plugged in.

I have tried to modify the file  /etc/modprobe.d/alsa-base.conf but this has not worked.


pd: in arch_64 (chakra)  I have the same problem. it´s a bug of alsa?

---

### Post by Antin on 2009-11-04
I concur, I have the exact same problem.

---

### Post by pavalgauti on 2009-11-06
hello

I have the same problem with my vostro
 does someboy have a solution for this problem

---

### Post by pavalgauti on 2009-11-06
hello 
have you found a solution for your sound problem

---

### Post by yawie on 2009-11-17
Same here with karmic

---

### Post by superuser on 2009-11-23
Same problem here.

It is really very annoying.

Hint: the sound chip in the vostro 1220 is
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

Anybody please help us.

superuser

---

### Post by nu_kru on 2009-11-30
with the hdaanalyzer, in the node 0x1f, in the widget control, i disabled "out", speaker turn off though headphones are plugged out. (it's my temporary solution).

PD: Report the bug to alsa bugtracking

---

