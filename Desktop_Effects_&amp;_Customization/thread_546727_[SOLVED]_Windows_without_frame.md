---
title: "[SOLVED] Windows without frame"
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by Amazona aestiva on 2007-09-09
Hi! I think the attached jgp tells my problem.

I've installed:
Beryl, Beryl-manager, Emerald, Compiz

I've installed Nvidia driver(glx). (It's working because Stellarium runs well.)
I've tried to change between beryl and compiz.
With and without Emerald.

It worked a mouth ago.

I'm using Feisty.

---

### Post by Lord Illidan on 2007-09-09
Try running emerald --replace in a terminal...what is the output?

---

### Post by Amazona aestiva on 2007-09-09
I've got no output... it hangs...

---

### Post by Lord Illidan on 2007-09-09
As in the entire X-server hangs?

Were you using beryl at the time or not?

---

### Post by Amazona aestiva on 2007-09-09
I've tried the command with and without beryl running.

I hit enter 12 min ago:

---

### Post by Lord Illidan on 2007-09-09
Hmm, strange..What do you use to start beryl?

---

### Post by Amazona aestiva on 2007-09-09
I start Beryl manager from apps. -> System Tools

---

### Post by sonsnix on 2007-09-09
Hi!

Since yesterday I've got the same problem. When I change to "flat file configuration" or something, in the compiz settings, it works again. Seems like gconf somehow messed up...

Is there any way to fix it?

Thanks!

---

### Post by sonsnix on 2007-09-09
Sorry, my fault, obviously the "decorator" option wasn't set for compiz. When it isn't set, the decorators like emerald will fail to start. I had excatly the same symptom as the thread starter.

---

### Post by Amazona aestiva on 2007-09-10
I really like Beryl! There is nobody who can help me?:(:(:(

---

### Post by Amazona aestiva on 2007-10-08
Hey guys, I SOLVED it!
Thanks you have given me some good idea.

In Beryl Manager: Advanced Beryl options>Rendering path>Copy
Then Reload Window-manager

---

