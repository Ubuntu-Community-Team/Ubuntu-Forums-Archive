---
title: "Alein arena truble"
date: 2005-12-04
forum: Gaming &amp; Leisure
---

### Post by Br0k3ndr34ms on 2005-12-04
when ever i run it this is waht happends



evan@ubuntu:/usr/local/games/alienarena2006$ ./AlienArena
using /home/evan/.codered/data1/ for writing
using /home/evan/.codered/arena/ for writing
execing default.cfg
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
sound sampling rate: 11025
./AlienArena: line 5:  8091 Bus error               ./crx +set game arena $*



anyone know what this means and how i can fix it?

---

### Post by Br0k3ndr34ms on 2005-12-04
does nobody here like to help me?
is it cause of my spelling?
is it because i'm new too linux so i'm dumb and ask stuff most people would know?

---

### Post by Harleen on 2005-12-05
No, it's probably because nobody knows a solution for your problem. I even didn't knew alien arena before your post. Thanks for pointing me to it. At least it works fine for me. :mrgreen: 

A Bus Error occures, if a program tries to access memory it isn't allowed to. This probably won't help you much... But the system function mmap() is known to be able to create bus errors easiely. And I remember reading many posts on this forum related to sound problems in Quake based games (mostly ET), that complained about a failed call of mmap.
So Quake 3 or Enemy Territory will probably fail with the same error. You don't have tried these games yet by any chance?

So maybe you should follow the advices in the countless "no sound in quake3/ET"-threads.
This one seems fine: [http://ubuntuforums.org/showthread.php?t=77217](http://ubuntuforums.org/showthread.php?t=77217)

---

