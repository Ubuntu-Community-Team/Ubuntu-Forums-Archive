---
title: "Card Troubles"
date: 2005-12-15
forum: Desktop Environments
---

### Post by Unverzagt05 on 2005-12-15
I also have a Dell inspiron 2650 laptop, its not so much the card i think that it is the PCMCIA adapter. it wont recoginze the card in the adapter, nor will the card show that the adapter is even working (2 LED's light up when hooked into the laptops), its a Motorola Model : MN825G.

---

### Post by Unverzagt05 on 2005-12-15
if you need any more information, or system specs, just leave a post.

---

### Post by zoiks on 2005-12-15
what is an MN825G?  And what are you trying to do?  And what have you tried so far?

---

### Post by Unverzagt05 on 2005-12-15
probably should have posted this in hardware, but the MN825G is my wireless PCMCIA adapter for my lappy. the problem im having is getting the laptop's PCMCIA slot to work. i haven't tryed anything as im new to this, and google.com/linux isn't giving me much help.

---

### Post by zoiks on 2005-12-17
[QUOTE=Unverzagt05]probably should have posted this in hardware, but the MN825G is my wireless PCMCIA adapter for my lappy. the problem im having is getting the laptop's PCMCIA slot to work. i haven't tryed anything as im new to this, and google.com/linux isn't giving me much help.[/QUOTE]

Googling for MN825G yields nothing.  Are you sure it's not a  WN825G?  This one yields tons of stuff on google.  It's possible one of these links will be helpful.
[http://www.techsupportforum.com/linux-operating-systems-applications/25435-wn825g-wpci810g-drivers-linux.html](http://www.techsupportforum.com/linux-operating-systems-applications/25435-wn825g-wpci810g-drivers-linux.html)
[http://www.suseforums.net/index.php?showtopic=16107](http://www.suseforums.net/index.php?showtopic=16107)

It appears this wireless card uses the broadcom chipset, which blows for Linux since there are no native drivers.  You need to use ndiswrapper for that card (which I have never used - only used atheros-based and ralink-based cards which work without ndiswrapper).  But your PCMCIA slot, per se, shouldn't have any problems in Linux.  Your system might not know what to do with some cards plugged into it, tho.

---

