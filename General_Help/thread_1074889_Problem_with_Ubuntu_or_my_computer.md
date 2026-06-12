---
title: "Problem with Ubuntu or my computer?"
date: 2009-02-19
forum: General Help
---

### Post by bkeller on 2009-02-19
Okay so I've had Ubuntu installed on my desktop for a little bit.  I started up my desktop today and it got into Ubuntu and I went about my business.  As I was doing stuff it suddenly hung, the mouse wouldn't move the keyboard didn't respond and the screen sat in place, so I did a hard reset.  Unfortunately it didn't POST.  After letting the computer sit for a little bit I restarted it and it was fine and happily went back into Ubuntu.  Sure enough though, less than a minute after logging in it hung again.  It seems that after every time it does this the computer has to sit off for a while before it will POST and operate normally.

edit:
I think I've ruled it down to 3 or 4 possibilites

1. Ubuntu - But that doesn't explain the lack of a POST after failing.
2. A bad sector on a hard drive (or something like that?)  - Still not sure if it would explain a lack of a POST.  The drive has been clicking rather loudly when the computer starts though.
3. Bad MOBO - Possible, that explains the lack of a POST but it doesn't explain why the computer works later :/
4. Processor - Not sure how it relates to the POST.  Maybe it's over heating.  I've checked the case temperature and it is fine though the heat sink of the processor is a bit dusty.

double edit:

It turned out to be the processor.  I decided to go ahead and clean the heat sink, when i popped it off the processor stayed behind.  I think the thermal glue was mostly gone :O  So....here's to hoping it still works when I get some more glue.

---

### Post by taurus on 2009-02-19
When you first boot your machine, there is a memtest option in the GRUB menu.  Run that to test your RAM.  Otherwise, the graphic card could be bad!

---

### Post by marshall.robert on 2009-02-19
Did you build this PC yourself? Because I have a feeling that it's the power supply, and that it's not powerful enough. I used to get these sorts of symptoms when running off a 250W when I should have had a 400W.

---

