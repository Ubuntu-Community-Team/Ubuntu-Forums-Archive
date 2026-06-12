---
title: "streaming audio using all my memory?"
date: 2005-08-09
forum: Desktop Environments
---

### Post by factotum218 on 2005-08-09
I was wondering if maybe having xmms playing streaming audio might be why 808MB of my 1 gig of ram is used, but when I typed the command  $top, i noticed this one line...

Python was at the top of the list using 75% of my memory, is this because of Rhythembox? Should I switch to something like xmms??

I tried killing Rhythmbox, but that just freed up 4mb...ugh. All else i have open is a gterm and firefox, why would Python be running? Its not as root, its as my user.

I did a kill 7644, for the PID through the "top"command, it killed gdesklets. This brought me back down to about 2/3 free. Is gdesklets really that memory intense or is this just a straight out python issue?

---

### Post by factotum218 on 2005-08-09
bump,

just looking for ideas. Gdesklets? Python? Rebel code from the depths of Acron, Ohio?

If you go to the Gnome Art section, I have a screenshot from yesterday with gdesklets running showing the 800+ megs of used ram. Kinda wierd.

---

### Post by blind0wl on 2005-08-09
Can you post your ```
top
``` output?  Might help in seeing what the problem is

---

