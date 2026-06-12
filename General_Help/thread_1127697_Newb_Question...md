---
title: "Newb Question.."
date: 2009-04-16
forum: General Help
---

### Post by mholtum on 2009-04-16
Without actually opening up my computer case is there somewhere
in Ubuntu where I can find out my processor speed, ram size.. all that
sorts of stuff?

---

### Post by ddrichardson on 2009-04-16
```
cat /proc/meminfo
cat /proc/cpuinfo
```

---

### Post by riza hylviu on 2009-04-16
with sysinfo -- [http://www.ubuntugeek.com/howto-get-your-system-information-with-sysinfo.html](http://www.ubuntugeek.com/howto-get-your-system-information-with-sysinfo.html)  -- there is an explanation here
and you can use ubuntu tweak too for some info.
may i ask you why are you still using ubuntu 6.10

---

### Post by mholtum on 2009-04-16
> **riza hylviu said:**
> with sysinfo -- [http://www.ubuntugeek.com/howto-get-your-system-information-with-sysinfo.html](http://www.ubuntugeek.com/howto-get-your-system-information-with-sysinfo.html)  -- there is an explanation here
and you can use ubuntu tweak too for some info.
may i ask you why are you still using ubuntu 6.10


Thank you. Well, my profile is out of date. I'm at 8.10.

---

### Post by 3Miro on 2009-04-16
```

sudo lshw

```

---

### Post by kiddykoff on 2009-04-16
if you don't want to go through terminal, (i avoid it when possible) go to 

system>administration>system monitor

it dosen't give you as much information as lshw, but it does give you the memory and cpu information

---

