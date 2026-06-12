---
title: "Counter-Strike: Source dedicated server problem"
date: 2007-07-16
forum: Gaming &amp; Leisure
---

### Post by Frongo on 2007-07-16
Hey guys,

I'm trying to install source dedicated server on my ps3 running Ubuntu Edgy using [[COLOR="Blue"]this[/COLOR]]("http://wolphination.com/linux/2006/03/29/how-to-setup-a-cssource-dedicated-server/") guide, but this is what happens when I get to the step that tells me to type: "./hldsupdatetool.bin".

root@playstation:/home/frongo/srcds_l# ./hldsupdatetool.bin
bash: ./hldsupdatetool.bin: cannot execute binary file
root@playstation:/home/frongo/srcds_l# sh ./hldsupdatetool.bin
./hldsupdatetool.bin: 1: Syntax error: "(" unexpected

I've looked around and I can't seem to find anyone else having this problem. I'm fairly new to the whole linux scene but I've been playing around with it for a bit. This is my second time installing linux on my ps3 and it's pretty easy by now.

Any help is appreciated :)
Thanx

---

### Post by ashmew2 on 2007-07-25
Hi man , i opened that guide and i doubt that the problem lies somewhere here :

where it says :

```
chmod +x hldsupdatetool.bin
```
i think u shud use :

```
chmod a+x hldsupdatetool.bin
```

followed by

```
./hldsupdatetool.bin
```

Not really sure on this one though , let me know if this helped !

---

