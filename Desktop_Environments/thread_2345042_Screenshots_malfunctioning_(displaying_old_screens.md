---
title: "Screenshots malfunctioning (displaying old screens no longer open)"
date: 2016-11-30
forum: Desktop Environments
---

### Post by jhwheeler on 2016-11-30
Hi Everyone,

I've searched quite a lot and haven't found anything like this. 

When I do PrtSc, it takes a screenshot of some old windows that are no longer open (and haven't been for hours). 

I tried uninstalling gnome-screenshot and using Shutter instead, but the issue persists. 

I'm on Ubuntu 16.04.

Any ideas as to why this would be happening?

Thanks!

Alacritas

---

### Post by Frogs Hair on 2016-11-30
Hello and Welcome

Do you see the same when you open the screen-shot application or just when you use the print screen key ?

---

### Post by jhwheeler on 2016-12-01
Thank you very much for your prompt reply.

To answer your question, it is also pretty strangely messed up when I use the screenshot app. It splits the screen in half, as if I were switching between two workspaces and it caught me in the middle. This also happens when I do it by drawing a selection on the screen - the "screen" it gives me to select from is not the screen I am actually viewing, strangely enough.

---

### Post by Habitual on 2016-12-01
for shutter, shut it down and open a terminal and issue:
```
rm -fr ~/.shutter
```
and fire up shutter and see if it persists.


What is the Video card and driver details? Any other uncommon visual anomalies?

---

