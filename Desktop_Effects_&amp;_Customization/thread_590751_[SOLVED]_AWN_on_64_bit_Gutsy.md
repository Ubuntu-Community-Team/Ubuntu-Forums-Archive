---
title: "[SOLVED] AWN on 64 bit Gutsy"
date: 2007-10-25
forum: Desktop Effects &amp; Customization
---

### Post by Inxsible on 2007-10-25
I installed AWN from source since I use 64 bit Gutsy and i think the repos only provide the 32 bit versions. I used reacocards guide for doing this.

I now have the Avant Window Navigator in my menu, but it does not start up. Neither does the avant manager

I have a fresh gutsy install, not an upgrade from feisty.
Running ```
avant-window-navigator
``` in a terminal give me this

```
inxsible@inxsible:~$ avant-window-navigator
avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory
inxsible@inxsible:~$

```Please help !

---

### Post by joshuachad on 2007-10-25
run $ sudo ldconfig

Cheers

---

### Post by joshuachad on 2007-10-25
BTW if you decide to install something else from source do the same thing when finished. Not just with AWN.

---

### Post by Inxsible on 2007-10-25
> **joshuachad said:**
> run $ sudo ldconfig

Cheers
What does this command do ?

---

### Post by joshuachad on 2007-10-25
the best way to find out is to man it i.e $man ldconfig

It updates your libraries.
Synaptic does this now after installing packages 



Cheers

---

### Post by Inxsible on 2007-10-25
> **joshuachad said:**
> the best way to find out is to man it i.e $man ldconfig

It updates your libraries.
Synaptic does this now after installing packages 



CheersDid the man. Thanks it works now :)

---

### Post by joshuachad on 2007-10-25
Great Have fun!

---

