---
title: "LyX Performance Very Slow"
date: 2010-10-06
forum: Education &amp; Science
---

### Post by bitterbug on 2010-10-06
I've been experimenting with LyX 1.65 and 2.0 and have been having some serious performance issues when trying to format a 90 page text document.

Any attempt to delete, cut/paste, etc. involves the application hanging for 20 to 30 seconds before completing the task.

I've read that versions of Qt can be an issue, as well as video drivers causing interference, but I've been testing on a desktop running 10.04 with an nVidia card and the Qt version default for that, as well as a netbook running 10.10 with an intel card, and the bleeding edge Qt.

Same behavior on both. 

Anyone else run into the same?



keywords: lyx latex wysiwyg formatting hang slow 1.65 2.0

---

### Post by ExCrusader on 2010-10-31
I am having the exact same issues. I don't have any solution to it yet. I am over 90 pages as well.

---

### Post by gordintoronto on 2010-10-31
A netbook has a grossly slow CPU, so any speed problem is easy to assign blame. What is the processor on your desktop?

---

### Post by ExCrusader on 2010-10-31
Copied directly from HardInfo:

-Processors-
AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53		: 800.00MHz
AMD Athlon(tm) 64 X2 Dual-Core Processor TK-53		: 800.00MHz

---

### Post by gordintoronto on 2010-11-01
However, the TK-53 can run at 1.7 GHz, so it should be (more than) twice as fast as a netbook for any program which can use multi-threading.

Have you considered dealing with a chapter at a time until you're ready for final output? I've done a lot of writing, but I'd get lost in a 90-page document.

---

### Post by ExCrusader on 2010-11-01
I have considered it, but then I would lose a lot of the automated functions (table of contents generation and the like). It is a good solution, but not a perfect one. I may have to see if they have somewhere to report bugs and bring this up.

-Edit-
I misunderstood what you were saying. Yes, I should be able to break it up into multiple pieces until it is finally edited and then put them all into one file (assuming it just goes slow and doesn't completely stall out on me) to create the pdf from it. Simple solution to the problem, thanks!

---

