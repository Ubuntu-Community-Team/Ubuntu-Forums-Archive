---
title: "My Ubuntu x64 setup is consuming WAY too much RAM"
date: 2009-06-17
forum: General Help
---

### Post by Dynelight on 2009-06-17
Hello. I'm using an Ubuntu x64 architecture. My hardware is currently an Athlon FX 2, 8GB RAM, Geforce GTX 9800.

I'm running it with Compiz, Emerald, AWK (Yeah I like eye candy so).

I can expect this setup to consume a lot of RAM. However, it's consuming nearly ALL of my RAM (7 Gigs!)

I'm assuming there might be a memory leak somewhere. Can you guys help me identify if this is the game?

Thanks a lot!

---

### Post by Cheesemill on 2009-06-17
Using all of your RAM is a good thing. If it wasn't being used there would be no point in having it!!

Linux handles memory differently to Windows, chances are nothing is actually using your RAM, it has just been reserved by the system for caching and other purposes.

Try running system monitor to see what is using your memory and post back (you can sort the processes by memory usage to see what is using the most).

---

### Post by Soul-Sing on 2009-06-17
a 64 bit system will take some more RAM. But not that many!
you could take a look at your systemmonitor: processes: all processes.
or run ```
top
``` in the terminal.

---

### Post by Dynelight on 2009-06-17
Thanks! I was freaked out =)

---

