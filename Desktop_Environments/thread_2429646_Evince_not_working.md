---
title: "Evince not working"
date: 2019-10-21
forum: Desktop Environments
---

### Post by pansmanse on 2019-10-21
Evince has stopped working after a re-install of 18.04. Any suggestions?

---

### Post by uRock on 2019-10-21
> **pansmanse said:**
> Evince has stopped working after a re-install of 18.04. Any suggestions?

Is it not opening? Please tell us more about what you're seeing?

---

### Post by pansmanse on 2019-10-21
Sorry, not written very carefully. 
Double click on .pdf and the wheel of hesitation circles for a few seconds and disappears.
Run evince from the launcher, likewise.
Run evince from terminal and message appears: 'Segmentation error (core dumped)'. (I've just discovered this one)
Not sure what to do with core dump or where it is.

---

### Post by #&amp;thj^% on 2019-10-21
A &#8220;segmentation fault&#8221; is when your program tries to access memory that it&#8217;s not allowed to access, or tries to . 
First give us more to go on:
```
apt policy evince
```
And lets see how this reads now:
```
apt-cache rdepends evince
```

---

