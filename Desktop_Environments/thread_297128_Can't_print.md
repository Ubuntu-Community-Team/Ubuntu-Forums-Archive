---
title: "Can't print"
date: 2006-11-10
forum: Desktop Environments
---

### Post by kc2idf on 2006-11-10
It's just that simple.... I can't print.  Almost.  I can print a test page, and zero other content.

Googling for this problem yields many hits asking the same qustion, and zero answers.](*,) 

Any print job, from any application except the printer properties page, results in the job state almost immediately changing to "Stopped:job-stopped".  All attempts to resume through: printer queue window, lpadmin, CUPS web page, result in nothing; the job never changes state.

For some reason, test print from the printer properties page works.

Been banging my head against the wall for a week on this one.  I have, luckily, preserved my Breezy install, and will revert to that if nothing comes of this very-last-ditch effort to get an explanation on what is going wrong.

Even if you only have some debug procedure suggestions (what log should I be looking at?) I would be grateful to hear **ANYTHING** other than reading one more post of someone having this issue.

Oh, before I forget, HW/SW:

Edgy Eft.
Canon BJC-4200 (using BJC-600 driver, which is recommended driver and works just fine under Breezy)
Via Epia MII-12000 MoBo.

C'mon, people, give me **something** to work with!

---

### Post by kc2idf on 2006-11-10
Update:  using lpr -l will get something to come out of the printer.  It seems to bomb when I try to send postscript, which hints at a problem with filtering.

---

### Post by kc2idf on 2006-11-10
Okay, it's working.

If someone, somewhere along the line, had just said, "don't use greyscale mode with a Canon printer", I could have saved myself a shitload of time.

---

