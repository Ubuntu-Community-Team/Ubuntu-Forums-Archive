---
title: "[SOLVED] Emerald wont load on startup"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by danisgood on 2007-08-19
Hi,
I have compiz fusion installed on my pc, and i have on startup
compiz --replace
and
emerald --replace &

which i found on a forum, i think emerald is trying to load before compiz and it wont start, i have to start it manually. how can i fix this so it will work when i log in?

Thanks,
Danny

---

### Post by Happy_Man on 2007-08-19
Right. In System --> Preferences --> Settings, move the entries around so that Compiz is before Emerald.

---

### Post by danisgood on 2007-08-19
theres nothing called settings, do you meen sessions or compizconfig settings

---

### Post by Happy_Man on 2007-08-19
> **danisgood said:**
> theres nothing called settings, do you meen sessions or compizconfig settings
Sorry, yeah, I meant Sessions. Jeez.... I should go get some food.

---

### Post by danisgood on 2007-08-19
compiz is just before emerald, but its still not loading up on startup :(

---

### Post by walkerk on 2007-08-19
```
compiz --replace && sleep 3 && emerald --replace &
```
or

```
compiz --replace -c emerald &
```

do either of those work?

if not try doing this in Sessions. 

Name: Compiz
Command: compiz --replace

Name: Emerald
Command: sleep 5 && emerald --replace

---

### Post by danisgood on 2007-08-19
compiz --replace -c emerald &

That one works, but i tried that one before and didnt do anything, will try it again and tell you what happens

---

### Post by danisgood on 2007-08-19
well tried it and dosent work, compiz loads up but emerald dosent, have to press alt+f2 and type emerald --replace &     for it to run then

---

### Post by Lithium17 on 2007-08-19
It loads fine on startup for me, and I didn't need to add anything or configure any settings.

---

### Post by Pena on 2007-08-20
I had the same problem. For me it was because for some reason gtk decorator replaces emerald after it loads.

Since i don't need gtk decorator i moved it from /usr/bin/gtk-window-decorator to /usr/bin/gtk-window-decorator.moved so system can't find it. Worked for me but dunno if someone has more elegant solution.

---

### Post by danisgood on 2007-08-20
omg thanks, it works now :)

---

