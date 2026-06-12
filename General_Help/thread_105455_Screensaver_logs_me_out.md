---
title: "Screensaver logs me out?"
date: 2005-12-18
forum: General Help
---

### Post by plcdfa on 2005-12-18
Hi everyone! Must be a really lame question, but is it possible that the screensaver (or anything else) logs me out of my current KDE session after being idle for some time? I haven't found anything like that in kcontrol, but it must be where I messed things up, as I didn't experience this problem earlier. I've enabled the composite extension in xorg.conf recently for window transparency, don't know if thats got anything to do with the problem. Thx in advance for the answers!

---

### Post by One Quick Question on 2005-12-19
Hmm.  This sounds questionable.  Are you running a GL screensaver?
Sounds like it's possible that the screensaver is crashing X, dumping you back into the kdm...

That eyecandy extension can cause a lot of weird conflicts...

---

### Post by aysiu on 2005-12-19
Do you have the "require password to stop" box checked in your screensaver preferences? (see attached image)

---

### Post by plcdfa on 2005-12-19
First of all, thanks for the replys. 
aysiu: no, I don't have that enabled.
One Quick Question: Seems possible to me, cos I tried to disable the screensaver completely, and that eliminated the problem. Now I gonna experiment with a non-opengl one and report back. :)

---

