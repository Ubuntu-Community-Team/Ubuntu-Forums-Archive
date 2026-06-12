---
title: "Computer giving me hell times"
date: 2009-06-23
forum: General Help
---

### Post by elliotn on 2009-06-23
Since I got this SIS Mobo with 778mb ram, amd 18ghz processor. This thing keep switching off, with ubuntu I work on it for about 20 minutes, when I try windows xp it shuts immedietely giving the blue screen of dead. Wtf might be.

---

### Post by abn91c on 2009-06-23
the RAM chips may be bad or the cpu, is  the cpu fan working? do you get beeping when the computer boots?

---

### Post by madjr on 2009-06-23
that sucks

check the temperatures, powerswitch connection, try in another case, etc.

is the sis mobo an all in one integrated board?

anyways i hate cheap sis stuff..

---

### Post by Swagman on 2009-06-23
Get a thin paintbrush and clean the cpu heatsink out.

Btw.. **18GHZ** ?

---

### Post by elliotn on 2009-06-23
Its an all in one mobo, I'll try the cleaning. Btw its not 18 but 1.8ghz excuse me

---

### Post by LowSky on 2009-06-23
> **Swagman said:**
> 
Btw.. **18GHZ** ?

That is some extreme overclocking!!! LOL :popcorn:


I would think its overheating, most likely the northbridge chip, but it could be a bad hard drive or RAM too. it could also be a capacitor, older computers sometimes go bad because of years of use. Check the motherboard for bad smells or corrosion. thoses are signs of something being wrong.

---

### Post by elliotn on 2009-06-23
Ohh and I get one beep only when I turn it on, mmm thats a normal beep

---

### Post by abn91c on 2009-06-23
> **elliotn said:**
> Ohh and I get one beep only when I turn it on, mmm thats a normal beep
start pc with half the ram(take one chip out, rotate them) to narrow down the problems and replace the cmos battery also.

---

### Post by LowSky on 2009-06-23
get a live CD and run the memory test... if the PC locks up or fails then you will know there is an issue with the

---

### Post by elliotn on 2009-06-23
I have ran the memory test, passed with no errors, have noticed that one ram is DDR1 and the other is DDR200 does that say a thing?

---

### Post by elliotn on 2009-06-24
Cant seem to resolve the problem

---

### Post by lightstream on 2009-06-24
Sounds very much like a hardware problem. if you have two sticks of RAM try it with just one of them - if the problem persists, try it with the other one. 

My feeling unfortunately would be the hard disk - if it has bad sectors or read failures, it can easily kill Windows and cause Linux to hang after a while. On linux, when it hangs, will it really hang for ever? Try leaving it for literally 15 minutes and see if it produces any error.

Try using it in Linux command line only - you may get more useful error messages appear (but again leave it for literally 10 minutes before deciding it is totally hung)

---

### Post by lightstream on 2009-06-24
Couple of other things to try: force a disk check (**sudo touch /forcefsck** then reboot)

If you have USB on your machine, make or get a bootable USB stick (with Xubuntu on or something). See if the system is stable when running from the USB. 

These should tell you whether the problem is indeed related to the disk drive (or the disk controller on the mobo)

---

