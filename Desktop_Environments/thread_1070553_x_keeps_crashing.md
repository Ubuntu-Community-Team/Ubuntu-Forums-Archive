---
title: "x keeps crashing"
date: 2009-02-15
forum: Desktop Environments
---

### Post by waylow on 2009-02-15
Hey Guys,

I'm having problems with x

it keeps crashing

I am running an older kernel 2.6.22-14  (anything newer than this - and my wireless card just will not work)

I have tried every driver but they all do the same thing
X will just randomly crash  every few minutes making it impossible to do any work

tried Nvidia 96, 173, 177, 180 - through the Hardware Drivers menu and also through envy

and also tried stopping X and installing 180.29 with the Nvidia installer 


My graphics Card is Nvidia Quadra FX 540
(do you need any other information - is there a dump or log file of the crash??)


cheers
waylow

---

### Post by waylow on 2009-02-16
oh and it also crashes if I use the generic driver

does anybody know how to help?

---

### Post by Kevbert on 2009-02-16
First thing to try is to run memtest. Do you have any other OS on the PC ? Does that crash ?

---

### Post by waylow on 2009-02-16
thanks for the response

I will run the memtest now
it's the 8.10 version - Memtest86 v2.01

I am dual booting with Windows which runs fine (even though it is windows ;) )

---

### Post by waylow on 2009-02-16
it seems to get about 200 errors each pass


I have never used memtest before - what does that mean?

---

### Post by Kevbert on 2009-02-16
With Windows you may be able to run OK, but may get the occasional unexpected crash. Memtest is quite a good way of testing the memory as it does a full and extensive test (unlike power on self-test or POST, when you first turn on the PC). You should not get any errors.
If the PC and memory are old the failures could be due to a build up of dust. You can remove this if you very carefully use a vacuum cleaner.  Another problem may be that the memory is not properly seated in its socket(s).  If you remove and refit memory be careful that you don't touch the edge connectors and that you are in contact with the case at all times to minimize static discharge. If you have a number of memory chips it is worth removing one and then re-running memtest. When you think you've found the faulty memory, try this in a known working socket as it may just be due to poor fitting. Also try a good memory chip in the socket that fails (just in case the socket is damaged).
You should run memtest for at least 2 full passes to make sure everything is working fine.
Good luck.

---

### Post by waylow on 2009-02-16
thanks kevbert

makes sense now
at least I know my drivers are working

I will find the dodgy RAM

waylow

---

