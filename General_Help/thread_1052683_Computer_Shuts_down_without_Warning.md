---
title: "Computer Shuts down without Warning"
date: 2009-01-28
forum: General Help
---

### Post by alexebird on 2009-01-28
Hi,

I have been having a problem with my desktop, and I was hoping someone in the community could suggest a solution.  Basically, it just shuts down without warning and it does it randomly, in both Ubuntu and XP.  That would tell me it isn't a problem with Ubuntu, but I didn't see a better forum to ask for help in than General Help.

I thought it might be bad memory, so I tried running with only one memory stick, and it still had the problem for both sticks.  Other symptoms are that sometimes a program will exit on it's own, other times it won't start and report a segmentation fault in the command line.  Any ideas?

Alex

---

### Post by Yellow Pasque on 2009-01-28
It sounds like your processor is overheating and there's a BIOS setting that shuts down the system when the processor reaches a certain temperature. Open your case and make sure that the CPU heatsink isn't clogged with dust and that the CPU fan is operating corrrectly.

---

### Post by Gizenshya on 2009-01-28
I think Temüjin is probably right.

but just so you can rule out RAM issues, in XP (or vista for that matter) if your RAM is bad you will see a blue screen shortly before it shuts off.  it might stay there for lessthan a second, but it will be there.

EDIT: also, if you put the heatsink on yourself, you might want to reseat it.  I had a similar problem with my current setup.  when I reseated the heatsink,I dropped about 7 degrees C and it took care of the problem

---

### Post by Peter09 on 2009-01-28
During grub boot, after hitting escape to get the Grub menu, you can scroll down (passed recovery mode) and select a ram test utility.

---

