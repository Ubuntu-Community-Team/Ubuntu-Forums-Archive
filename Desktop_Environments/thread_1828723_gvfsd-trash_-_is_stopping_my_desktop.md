---
title: "gvfsd-trash - is stopping my desktop"
date: 2011-08-19
forum: Desktop Environments
---

### Post by nicolasdiogo on 2011-08-19
i have this process running on my ubuntu box nad it is making my desktop to be very unresponsive.

```

28082 be/4 MYUSER    920.44 K/s    0.00 B/s  0.00 % 90.76 % gvfsd-trash --spawner :1.13 /org/gtk/gvfs/exec_spaw/0
```

i have reniced this process downwards - but it does not stop.

any suggestion on how i can investigate this?

it is meant to be the 'garbage collector' of gnome as i understand it and i should run constantly but not at the cost of my enjoyment.

thanks

NIcolas

---

### Post by jerrrys on 2011-08-19
seems to be multiple bug reports concerning gvfsd-trash going as far back as Hardy.  looks like your in a tough spot.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gvfsd-trash&sa=Search&cof=FORID:9#956](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=gvfsd-trash&sa=Search&cof=FORID:9#956)

---

