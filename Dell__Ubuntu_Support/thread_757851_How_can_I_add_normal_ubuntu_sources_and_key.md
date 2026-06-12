---
title: "How can I add normal ubuntu sources and key"
date: 2008-04-17
forum: Dell  Ubuntu Support
---

### Post by benste on 2008-04-17
My friend bought a Inspirion 15xx or so with ubuntu 7.10.
I was very angry when there where couple of mistakes in synaptics like "couldn't install "vlc or so" because package yyy could not be installed because it depends on zzz which is not aviable"

i looked into the sources (added Medibuntu)
and saw that there are only dell sources wich seems not to have all packages!!
How can I add normal ubuntu sources with key?
+ Lin DVD can't play DVD!!
+Rhytmbox can't play mp4 (my 8.04 version can play)


Please help me

PS: is it normal that the notebooks grafic chipset is blacklisted for compiz??? this was the only thing why my friend bought it !!!!
He's thinking of changing to M$ again, so hurry up and help.

(He's new to Ubuntu  and I'm using it for 2 years, but only with GUI :-()

---

### Post by mssever on 2008-04-18
> **benste said:**
> My friend bought a Inspirion 15xx or so with ubuntu 7.10.
I was very angry when there where couple of mistakes in synaptics like "couldn't install "vlc or so" because package yyy could not be installed because it depends on zzz which is not aviable"

i looked into the sources (added Medibuntu)
and saw that there are only dell sources wich seems not to have all packages!!
How can I add normal ubuntu sources with key?
+ Lin DVD can't play DVD!!
+Rhytmbox can't play mp4 (my 8.04 version can play)


Please help me

PS: is it normal that the notebooks grafic chipset is blacklisted for compiz??? this was the only thing why my friend bought it !!!!
He's thinking of changing to M$ again, so hurry up and help.

(He's new to Ubuntu  and I'm using it for 2 years, but only with GUI :-()I don't know how to get the keys, but the following sources.list lines are in an normal setup (I've modified mine a bit, so I don't know EXACTLY what the normal setup looks like, but these are equivalent). If you don't have the keys, APT will nag you, but it'll still work.

```
deb http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
```

---

### Post by benste on 2008-04-18
I don't want apt to neck my frined, so how can I add these sources with key!!

---

### Post by MikeyMike01 on 2008-04-19
System > Administration > Software Sources > Third-Party Software

---

### Post by benste on 2008-04-19
I know this way BUT which key should be added???

---

### Post by drsaamah on 2008-04-19
the code above that was provided by mssever is EXACTLY what you need.  and if you're friend hasn't gotten too comfortable with customizing his computer i would HIGHLY suggest that you install a normal version of ubuntu.  i started off with the dell version and its garbage.  all it does is mess around with your sources and add stupid s*** that you dont need.  as for the blacklisted graphics card, did your friend order the nvidia card or the intel?

---

### Post by benste on 2008-04-19
There was only an intel chipset aviable,
I'm thinking of reinstalling with 8.04

HAs someone experiences with 8.04 on a Dell?

with 7.10 his I-Pod crashed, on my sony the I-Pod appeared with rhytmbox:-)

---

