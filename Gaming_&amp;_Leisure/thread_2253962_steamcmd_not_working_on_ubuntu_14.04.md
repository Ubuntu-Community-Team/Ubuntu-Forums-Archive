---
title: "steamcmd not working on ubuntu 14.04"
date: 2014-11-23
forum: Gaming &amp; Leisure
---

### Post by michael146 on 2014-11-23
I just got a supermicro server and since ubuntu server 14.04 doesn't have the graphics drivers for it, I installed ubuntu 14.04 64-bit. I was trying to set up a gmod server with steamcmd. I installed lib32gcc1 and libc6-i386 first, so that it could read steam's 32-bit libraries, and then continued setting it up. It got to the part where I can start the server, but everytime I try, I get this:

./srcds_linux: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

I know it has to do with steam's 32-bit libraries since I have 64-bit ubuntu, but I installed the 32-bit libraries. any ideas?

 the server has 4GB ram & 320gb HDD. the rest of the specs of the server can be found here (the motherboard specs):
[http://www.supermicro.com/products/motherboard/ATOM/ICH9/X7SPA-HF-D525.cfm](http://www.supermicro.com/products/motherboard/ATOM/ICH9/X7SPA-HF-D525.cfm)

---

### Post by SirMoo on 2014-11-25
Try installing package *lib32stdc++6*

You should really just run the server on ubuntu server and not with a gui... Slight learning curve at first... but it's not bad once you get the hang of it.

---

### Post by michael146 on 2014-11-25
Thanks so much. It worked. Also, ubuntu server doesn't have the proper graphics drivers for this server so when I tried to install it, it just had a blinking cursor.

---

