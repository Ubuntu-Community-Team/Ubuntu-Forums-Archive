---
title: "i need help dual booting windows 98 and ubuntu with out opening up the case and chang"
date: 2009-02-13
forum: Desktop Environments
---

### Post by glooorfindel on 2009-02-13
i need help dual booting windows 98 and ubuntu with out opening up the case and changing the hardrive that boots

---

### Post by nevada1920 on 2009-02-13
:lolflag: it is hard to dual boot any microcrap as i call :lolflag:

lol lol ~!!!!!!!!!!!:confused:

---

### Post by lykwydchykyn on 2009-02-13
That should be perfectly doable; what seems to be the problem you're running into?

---

### Post by Dougie187 on 2009-02-13
It's not hard to set up a dual boot. I don't know about with windows 98 though. If you want to try it, just install windows 98 like you normally would (only on a partition of the hard drive instead of the full thing, which you can see up when you install windows or you can boot to the live cd of ubuntu and use gparted to do it). After you have Windows 98 installed, then try installing ubuntu. I am not sure if grub picks up windows 98 partitions or not, so if might work after you finish that, but if it doesn't im sure you can post your issues here and someone can help you out.

---

### Post by itendo on 2009-02-13
As I recall 98, it was particularly bad about scattering data all over the hard drive and the defrag util not doing much about it. If youre looking for an install squeezing all of that data into a good physical space is going to require a serious defragger. 

I would get yourself some partition magic or other editor. I like the ubuntu util, but my ms-brain didnt trust it. by the second computer i was fine with dual boot installing.

but aside from those two steps, the live cds work like magic.

---

### Post by Charles4809 on 2009-02-13
When you power up your computer you will see some remarks: push Del or F1  or something like that to enter the BIOS. It would be even better if there is a remark that tells you: push this to enter Bootpriority.

Well, either directly or through the Bios you can change which drive your computer will use as the first one to start from.

But I wonder why there is no GRUB-screen at start up, usually it's installed when you install Ubuntu.
Let us know if this worked for you.

---

