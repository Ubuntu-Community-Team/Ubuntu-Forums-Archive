---
title: "How to autorun program at boot up Ypops"
date: 2009-01-26
forum: General Help
---

### Post by theedudenator on 2009-01-26
I have to open a terminal and run this command to have YPOPs working

sudo /etc/init.d/ypops start


Can I make this so it starts when I reboot?

---

### Post by dagnabit dang doohickey on 2009-01-27
```
update-rc.d ypops defaults 99
```

BTW: Does that thing even work for you? I tried using it some months ago with no luck at all.

---

### Post by theedudenator on 2009-01-27
It works perfect after I manually start it

---

### Post by theedudenator on 2009-01-27
pete@XPS:~$ update-rc.d ypops defaults 99
 System startup links for /etc/init.d/ypops already exist.
pete@XPS:~$

---

### Post by dagnabit dang doohickey on 2009-01-28
I'm vaguely remembering the problem I had with ypops was that it never seemed to be running no matter what I tried. I completely gave up on ypops and opened a gmail account.

---

