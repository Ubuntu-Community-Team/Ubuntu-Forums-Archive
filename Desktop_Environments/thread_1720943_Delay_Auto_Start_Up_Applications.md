---
title: "Delay Auto Start Up Applications?"
date: 2011-04-03
forum: Desktop Environments
---

### Post by Thehuntedqwert on 2011-04-03
Hey I'm a mid level ubuntu user, basic script skills and I need some help with start up applications. 
 
I have it set up to start my music player (RBox) and torrent program (Transmission) when I log in. The problem is all my data is set on my 1TB external hard drive, because my internal hard drive only has 80GBs of space. When I start up the programs open but the external hasn't had time to link the file directories which messes screws up my torrents into having to verify every time and my music has to "recalibrate" as it were.
 
This isn't an issue when I manually open the programs after a minute or so but what my question really comes down to is... Is there a way to delay an automatic startup? Say, run application 3 minutes into boot up?
 
Thanks for all your help

---

### Post by Krytarik on 2011-04-03
You could use the command "sleep" for that, simply put the "command" for the launcher like this:
```
sh -c "sleep 3m; rhythmbox"
```
Greetings.

---

### Post by Thehuntedqwert on 2011-04-04
Thank you, worked like a charm

---

