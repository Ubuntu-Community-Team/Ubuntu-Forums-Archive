---
title: "black screen upon startup"
date: 2009-02-05
forum: General Help
---

### Post by griffnmzr on 2009-02-05
For no apparent reason I had my laptop running 8.10 freeze completely.  I waited for awhile then manually shut it down.  When I tried to turn it on again, I found that nothing would show up on the screen at all.  

The screen was entirely black but after a few tries, it began to flicker.  Eventually I was looking at a very low quality image of the normal start up screen except it would flicker on for a less than a second then flicker off again for more than a second.

I eventually saw a dialogue telling me that there was a graphics profile issue but I really could not do much about it.

I am a college student and my laptop contains all the work for my classes.  Figuring out this problem quickly is essential.

---

### Post by nytek on 2009-02-06
You might want to try and reconfigure X. 

Just boot ubuntu and get to the grub menu. Boot it in recovery mode and there is an option to restart X. 

Try this and see if it works. 

Good luck.

---

### Post by griachae on 2009-09-21
hey i got ubuntu 9.04 and its quiet good. 

but after installing catalyst control center (ati driver) it kicked my screen after restarting (grafic doesnt work and then i got a black screen without any reaction to any commands). :confused: 

when i start with bootloader i cant enter the terminal to prefix my problem. theres always a autostart into the desktop which turns into a black screen...

i read it may be that there is a conflict between the ati driver and fglrx...

so what should i do ?

thx in advance
---------
grafic: ati hd 4850
cpu: amd phenom x3
ram: 2 gb
screen: samsung fhd 94cm

---

### Post by P4man on 2009-09-21
try the latest ATI drivers from ATI's website. It seems like the drivers recommended by jaunty are too old or buggy to work with the latest ATI cards. On the ATI website you'll find a detailed PDF explaining how to install those.

---

### Post by griachae on 2009-09-21
ok ill try that and tell you if it works\\:D/

---

### Post by griachae on 2009-09-21
> **P4man said:**
> try the latest ATI drivers from ATI's website. It seems like the drivers recommended by jaunty are too old or buggy to work with the latest ATI cards. On the ATI website you'll find a detailed PDF explaining how to install those.

well i downloaded the driver but how can i install it without the treminal (because i still cant enter it with any key combinations) ? 

theres a code given from ati: ```
sh ./ati-driver-installer-9-9-x86.x86-64.rum
```

but when i added this code into the bootloader it didnt work...:confused:

---

