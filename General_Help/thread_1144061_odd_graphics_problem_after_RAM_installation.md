---
title: "odd graphics problem after RAM installation"
date: 2009-04-30
forum: General Help
---

### Post by tbonepower07 on 2009-04-30
I have an old Dell Dimension 2400 (Pentium 4, Intel integrated graphics). I installed Xubuntu 8.10 on. It was really pokey but ran. I upgraded the RAM by 512MB to 768M, and ran the memtest option from Grub (it passed).

Shortly after booting, Xubuntu would freeze, and the screen was covered in horizontal static (picture below). (This happens every boot)

[IMG]http://www2.bc.edu/~wimberle/error.jpg[/IMG]

Hoping it would work better I made an Ubuntu 9.04 install CD and booted it. This too had graphical problems, but instead of thin horizontal lines it would freeze with thick vertical bars:

[IMG]http://www2.bc.edu/~wimberle/error2.jpg[/IMG]

Is this a problem with the RAM, even though it passed the memtest in Grub?

---

### Post by freonchill on 2009-04-30
try swapping the memory in the slots...

---

### Post by xRes on 2009-04-30
I think it's preferred to have ram sticks that are the same size and frequency which I assume is not the case here? 
Have you tried swapping them around?

---

### Post by sedawk on 2009-04-30
It is very likely, that your internal graphic chipset reserves
some of your memory for graphics. It is possible that this memory
is not available to the memtest tool, so it cannot be tested.

What you can try is
* Check the module timing and compare it to the BIOS setting
  (Set to slower module's timing). Is there some kind of
  "auto-timing" vs. manual settings?
* Swap the two modules (e.g. some (older) PCs
  required the bigger module(s) to be installed in the "lower" banks)
* Run with only one module installed (256 or 512)

I had a very similar problem when adding a 1 GB module to a 512 MB module.
Nothing really worked, so I used that PC with only the 1 GB module.
A few months later I added the 512 MB module again and suddenly everything
worked. I still do not know why!

---

### Post by tbonepower07 on 2009-04-30
Thanks! Swapping the cards works. So I'm guessing when the cards are different sizes, I might have had the larger card in the 2nd slot, and this causes addressing problems?

---

### Post by freonchill on 2009-04-30
good. glad that fixed it.

typically having the bigger stick in the primary slot works better, never had a problem where it actually caused problems, but then again, it was being used for the on-board video.

---

### Post by tbonepower07 on 2009-04-30
Sedawk - Thanks for your post too, I was in the process of switching the modules when you posted your help. I'm installing Ubuntu and I reboot it I'll check the module timing stuff to try and prevent further problems.

---

### Post by xRes on 2009-04-30
I would agree, keep the larger of the two in the primary slot. Also remember that the ram speed will only be running at the lowest rate DIMM. I'm assuming that the smaller of the two is something taken from an older machine, so you may notice performance issues.

---

### Post by tbonepower07 on 2009-04-30
When I bought the new ram I looked on the computers info page on Dell to make sure I bought the right version, number of spins, speed (333MHz IIRC) to avoid problems, the only thing I changed was I got a 512MB card because it said that was the maximum supported. So I think the two cards are at the same speed.

---

