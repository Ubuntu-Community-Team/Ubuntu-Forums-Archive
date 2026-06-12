---
title: "NVIDIA NV15GL (quadro2 pro) + Compiz"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by frankzen on 2007-11-11
I am running the NVIDIA NV15GL card on Gutsy. Is it possible to get Compiz running on this card?

I have tried setting up the restricted drivers, but when the system reboots, it comes up in 640x480 and 800x600 and nothing else is available.

I also tried DL'ing the legacy drivers from Nvidia and installing that way. Same thing. Maybe there is not enough memory on the card (32 megs I believe) ?

Funny thing I get better resolution on my Debian Sid installation, but haven't tried Compiz on that system.

Help anyone ?

---

### Post by frankzen on 2007-12-15
Guess not.

---

### Post by theRightNee on 2008-01-03
hey hang in there pal
i too am experiencing the same issues you are 
i have no idea what is wrong
perhaps the legacy drivers cannot function with the card?
i am lost :confused:

---

### Post by theRightNee on 2008-01-03
btw, there should be more screen resolutions even if there isn't enough memory, but here i am stuck at 800 x 600

---

### Post by theRightNee on 2008-01-03
ok i got it fixed...
i don't know how, but i booted to a low graphics interface, where i could configure the display.
the OS could not recognize my display, and i think that is your problem as well.

now the beryl-compiz thing is a whole different animal in my case.
i cannot get anything to work. i am pretty sure it can at least run normal, and the legacy drivers do not seem to be the best way to go. if you look under synaptics, you will find a nvidia-glz-new package that seems to be better...though it hasn't worked out for me, so i don't know

---

