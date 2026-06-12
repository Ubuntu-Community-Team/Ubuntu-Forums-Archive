---
title: "Vostro 1000 - Wubi horizontal flickering"
date: 2009-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Boulemans on 2009-05-29
I've just installed wubi 9.04 on my dell vostro 1000 laptop. All looked ok, but after my first log out this happened:

my screen created a "double image" - I can see the normal screen, and a light version of it. The light version has moved a little to the left, and is flickering constantly (only the "light" version is flickering). I don't have any idea what it could be. Can someone redirect me to the thread with a possible solution? (for the record: this problem is not happening on windows vista - so there must be a solution) 

more specs:
Dell Vostro 1000
:: Processor
AMD Athlon 64 X2 (Hawk-256) TK-53 1.7 GHz
:: Motherboard
ATI RS480
:: memory
1024 MB, Nanya 1024MB PC-4300 DDR2, 2x512MB
:: graphical
ATI Radeon Xpress 1150 - MB, Core: 100 MHz, Geheugen: 400 MHz, up to 320MB Shared Memory
:: Screen
15.4 Zoll 16:10, 1280x800 Pixel, mattscreen

---

### Post by Blue Sassley on 2009-05-29
Have you checked System --> Administration --> Hardware Drivers to see if Ubuntu can find a Restricted ATI driver for your video card? I've also seen this on some of my laptops with Ubuntu trying to use the wrong screen resolution.

Blue

---

### Post by Boulemans on 2009-05-30
Thank you for responding, Blue Sassley,

> **Blue Sassley said:**
> Have you checked System --> Administration --> Hardware Drivers to see if Ubuntu can find a Restricted ATI driver for your video card? [...]

I didn't found anything for ATI there, only the restricted driver for the Broadcom WLAN is in the list (which is activated). 

But it seems to me that the problem fixed himself: after last night, there is nothing left of this problem: Ubuntu is working just fine. Can it be that Ubuntu solved the problem by himself, or is it waiting to start over again?

greetings

---

### Post by Blue Sassley on 2009-05-30
Could be, did you receive any new updates?

Blue

---

### Post by Boulemans on 2009-05-31
Yes, that was the case!

---

### Post by Blue Sassley on 2009-05-31
Maybe tag this as solved?

Thanks,
Blue

---

### Post by Boulemans on 2009-06-01
Oh, it's not so solved as it looked to mee. When I log in as a guest, the problem occurs again. Can updates be user-related?

---

