---
title: "KDE 3.4 hogs too much resources"
date: 2006-02-02
forum: Desktop Environments
---

### Post by CPUFreak91 on 2006-02-02
Hi, how can I lower KDE's resource hogging? This is on a Dell Latidude with 256 MB ram and 256 MB swap.

---

### Post by Lord Illidan on 2006-02-02
256 mb swap is too little, that's one thing.

And does it run too slow, or it seems to take up too much RAM?

Can you show us a screenshot of Ksysguard, too?

---

### Post by Choad on 2006-02-02
[QUOTE=Lord Illidan]256 mb swap is too little, that's one thing.

And does it run too slow, or it seems to take up too much RAM?

Can you show us a screenshot of Ksysguard, too?[/QUOTE]
lolzords 256 isnt too little to run kde

i have a laptop running debian and kde with 128 just fine

256 is too little for ubuntu maybe

---

### Post by Teroedni on 2006-02-02
Ive run Kubuntu a little, but i thiink that Kubuntu at startup loads Amarok
I f you remove Amarok you may get better perfomance and less resource hogs.


However with only 256mb ram your bond to get trouble

I would recommend that you install xubuntu instead.It use program which is more suited at low memory machines.

---

### Post by glycoknob on 2006-02-02
take a look here: [http://www.linuxjournal.com/node/8322/print](http://www.linuxjournal.com/node/8322/print), disable uneccary services that use a lot of memory, if you don't have a printer nor bluetooth you can disable these services. 
take a kernel matching your cpu i.e. if you have an pentium or better take a version for an 686.

disable all kinds of kde fancy stuff. kcontrol, appeareance disable there all gui effects, you won't miss them. 
use a fast kde style, keramik or kde classic are much faster than plastik, at least for me here
disable any kind of transparency.

disable the kde sound system. sound should work fine through, if not even better.

if your applications start slow install prelink and run it by sudo prelink -amR it will take a while but its worth trying. 

well maybe updating to kde 3.5.1 gains a performance improvement too, at least for me it did.

---

### Post by Lord Illidan on 2006-02-02
[quote=Choad]lolzords 256 isnt too little to run kde

i have a laptop running debian and kde with 128 just fine

256 is too little for ubuntu maybe[/quote]

Yes, but 256 MB of **swap** space.. (notice the emphasis) is too little. Generally, swap space should be twice the amount of installed memory.

---

### Post by CPUFreak91 on 2006-02-03
Thanks guys. I'll up the swap and remove some processes

---

