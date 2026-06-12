---
title: "replace metacity with emerald and compiz"
date: 2009-12-26
forum: Desktop Environments
---

### Post by FreezWay on 2009-12-26
I'm getting a new gfx card (yes, it has drivers) and I want to run compiz and emerald at startup instead of metacity. currently i alt-F2 and type "compiz" then alt-F2 again and type "emerald --replace" is there a way to bypass all this and not load metacity in the first place and instead load compiz and emerald?

---

### Post by doas777 on 2009-12-26
most folks just add emerald --replace to system -> preferences -> startup applications.

---

### Post by FreezWay on 2009-12-26
ok. seems sorta roundabout to load metacity then kill it and load emerald. I'll see if that works.

UPDATE: compiz loads but emerald doesn't...

---

### Post by doas777 on 2009-12-26
I think they do it that way on purpose, as metacity has no special requirements (unlike compiz). lets say you upgrade your kernel but haven't reinstalled your proprietary vidcard driver yet. you would not be able to get on a desktop since compiz can't load.
just a hunch tho

---

### Post by FreezWay on 2009-12-26
hmmm.... why wont emerald load though?

---

### Post by stinkeye on 2009-12-26
> **FreezWay said:**
> hmmm.... why wont emerald load though?

Install fusion-icon
```
sudo apt-get install fusion-icon 
```

Run fusion-icon...  menu -> system tools
Right click on fusion-icon in notification area and
select window manager -> compiz
select window decorator -> emerald

Add fusion-icon to startup applications using ```
fusion-icon -n
```

Should boot into compiz + emerald.

---

### Post by FreezWay on 2009-12-26
thx that works great!

---

