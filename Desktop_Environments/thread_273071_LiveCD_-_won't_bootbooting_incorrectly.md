---
title: "LiveCD - won't boot/booting incorrectly"
date: 2006-10-07
forum: Desktop Environments
---

### Post by ________ on 2006-10-07
Not sure if this goes under Desktop Support or Installation Problems, because my predicament is that I never even *reach* the installation phase.

The LiveCD for Ubuntu Dapper Drake 6.06 won't boot. That is, it commences booting, but never completes. This has happenend with three different computers, one that is 7 years old, another that is 5 years old, and one that is 1 year old. (the first and last mentioned were both top-of-the-line when purchased, the last one can still be somewhat considered as such) Three different LiveCDs were used, all from the same party of five, obtained via the ShipIt service. These are the experiences I have had with them:

Computer#1 (notebook computer) : LiveCD inserted, reboot, CD boots. Start or Install Ubuntu option selected, booting continues until the point upon which it has loaded both the Window Manager and Nautilus. Screen goes blank, there is some activity, nothing happens during following hours. Scenario repeated multiple times.

Computer#2 (notebook computer) : Exact same procedure as above, exact same result. Only one attempt to boot LiveCD.

Computer#3 (stationary desktop computer) : LiveCD inserted, reboot, CD boots. Start or Install option selected, CD loads... And suddenly the screen becomes a veritable mess of colors. An attempt to turn off computer fails, I have to pull out the plug. 

As mentioned earlier, several CDs were used. I suspect a bad party of CDs, however, with my limited experience, I can easily be mistaken.

Two questions:
(1) Has this sort of thing happened to many others, or is it an uncommon problem?
(2) Does anyone have any suggestions as to what the problem may be, and how I would go about to fix it?

---

### Post by CatKiller on 2006-10-07
There's an MD5 hash check on each cd so that you can check that the data on them is the data that is supposed to be on them.

Notebooks often have finicky hardware, which is why the OS is usually pre-installed and configured by the people that made them. Try a search for the model numbers to see if other people have reported how to get it to work on those particular machines.

There is, if I recall correctly, a safe graphics mode that might help you to diagnose the problem with the desktop computer.

---

### Post by ________ on 2006-10-07
I have checked the CDs for faults - nothing happens.
Safe Graphics mode - doesn't boot
Searching the web - Evidently at least three other people have been able to make it work on their computers, but it doesn't in the least tell me how to make it so on mine.

My Computer#1 (notebook computer) is an Acer TravelMate 721TX. (some clueless soul installed WinXP on it, despite its obvious age)
Computer#2: (notebook computer) unknown model (!) with WinME installed.
Computer#3: (stationary computer) Dell Dimesion DIM9100 with WinXP installed.

---

### Post by CatKiller on 2006-10-07
> **________ said:**
> I have checked the CDs for faults - nothing happens.

Do you mean that really nothing happens, or that it does some stuff but doesn't print an error message? I'm afraid I haven't used this, so I don't know exactly what it shows.

> Safe Graphics mode - doesn't boot
Searching the web - Evidently at least three other people have been able to make it work on their computers, but it doesn't in the least tell me how to make it so on mine.

My Computer#1 (notebook computer) is an Acer TravelMate 721TX. (some clueless soul installed WinXP on it, despite its obvious age)
Computer#2: (notebook computer) unknown model (!) with WinME installed.
Computer#3: (stationary computer) Dell Dimesion DIM9100 with WinXP installed.

What graphics card have you got in the Dell? It sounds like it might be a graphics card crash to me, but I've never actually experienced such a thing. At what point does it fail to load when you try the safe graphics mode? Perhaps there's some clue there.

I've never even heard of the integrated graphics in the Acer. Sorry.

---

### Post by ________ on 2006-10-07
I mean that it though it does stuff, everything checks out fine.

In the Dell, I have a Nvidia GeForce 6800, though I most shamefully  forgot to try booting it in safe graphics mode on the Dell, probably due to my frustrations with trying out various solutions with the Acer for several days. (I tend to use forums, the internet, tech support - whatever - as a last resort. I prefer figuring it out myself)

---

### Post by az on 2006-10-07
You need a minimum of 256 megs of ram to install.  How much ram do those computers have?

---

### Post by ________ on 2006-10-07
Computer#1 and #2 have an entirely unknown amount of RAM, and at first I thought insufficient RAM to be the problem. However, Computer#3 (Dell) has 1024MB RAM, so this cannot be the case.

---

### Post by lawina on 2006-10-07
Your Travelmate specs state that it has a Pentium II (333MHZ) CPU and RAM anywhere between 64MB to 256MB.

This is too low of a requirement in order for Ubuntu to work on it. 
Please try using Damn Small Linux(DSL) ([http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)) which has a smaller footprint and smaller requirements for hardware such as yours.

---

### Post by ________ on 2006-10-11
Sadly, there is no ShipIt service for this, and both my finances and blank CD store is quite... lacking.

Also, this does not explain the problems experienced by the other computers.

---

### Post by CatKiller on 2006-10-12
> **________ said:**
> Sadly, there is no ShipIt service for this, and both my finances and blank CD store is quite... lacking.

If you've got, or can borrow from a friend, one of those USB thumbdrives you may be able to boot DSL from that - depending on the configuration of those computers.

> Also, this does not explain the problems experienced by the other computers.

It might. You don't know how much RAM either of the laptops has, so they might both be inadequate. You said that the computer that did have sufficient RAM was expressing different symptoms, which indicates that that one might be experiencing a different problem.

Depending on where you live, you may have a local Linux Users Group who have already downloaded copies of different GNU/Linux distributions that you could use. Damn Small Linux will run on pretty much anything - it's tiny - but it is a bit scary-looking. You could try the Alternate cd - this installs in a text mode that is more likely to work. Also, Xubuntu has lower requirements than Ubuntu, so that might work on your laptops.

---

