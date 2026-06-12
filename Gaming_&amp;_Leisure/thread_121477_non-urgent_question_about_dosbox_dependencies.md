---
title: "non-urgent question about dosbox dependencies"
date: 2006-01-25
forum: Gaming &amp; Leisure
---

### Post by andrewc2005 on 2006-01-25
Alright this is kind of embarassing, 5 years ago I would have known what to do but I have unfortunately forgotten like 95% of my linux skills since then.   I was running dosbox, and having absolutely no problems with it, until I installed a couple of other programs via synaptic and it wouldn't load.  The only way I could get it to work was to completely recompile the program.  So it works but I'm still curious as to what went wrong initially, in case it happens again with another program.

I got this error:

dosbox: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

locate libGL.so.1 shows me:
/usr/lib/i686/mmx/cmov/libGL.so.1.2
/usr/lib/i686/mmx/cmov/libGL.so.1

with libGL.so.1 being a link to libGL.so.1.2.  So I added /usr/lib/i686/mmx/cmov to PATH, and I still get the error message.  Like I said the new version I compiled works fine but I don't get what the problem was initially and I'd like to know for future reference.

---

### Post by Perfect Storm on 2006-01-25
That indeed sounds fishy. Have you something new added to your sourcelist from an unofficial source?

---

### Post by andrewc2005 on 2006-01-25
[QUOTE=Artificial Intelligence]That indeed sounds fishy. Have you something new added to your sourcelist from an unofficial source?[/QUOTE]

I haven't installed anything between the time it was working and the time it broke except through synaptic (which on my box is configured to use just two repositories, the officially supported and the community/universe one).

---

### Post by Perfect Storm on 2006-01-25
It should be /usr/lib/libGL.so.1
Try look in /usr/lib/ if it's not there make a symblink and see what happens

---

### Post by andrewc2005 on 2006-01-25
[QUOTE=Artificial Intelligence]It should be /usr/lib/libGL.so.1
Try look in /usr/lib/ if it's not there make a symblink and see what happens[/QUOTE]

Cool, that worked when I tried it with stratagus, which just gave me the same error.  I'm still not sure why it couldn't find it before, unless the programs themselves are hardcoded to look in /usr/lib (in which case why would some other program install it somewhere else).  Oh well. 

But thanks for the help.

---

