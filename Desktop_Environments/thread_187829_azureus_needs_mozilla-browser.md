---
title: "azureus needs mozilla-browser?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by nubbe on 2006-06-03
Hi!

synaptic wants to add the package mozilla-browser when i want to install azureus.
Anyone know why?
am I just fuzzy?
:)

---

### Post by david_e on 2006-06-03
Don't know why: it's the same under kubuntu... moreover I was able to install Azureus only with this How-To:

[http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

installing Sun Java manually because the one installed from repo's had the "disappear when in system tray" problem...

---

### Post by ebash on 2006-06-03
I guess that it's because Azureus is using SWT as a graphical toolkit which requires mozilla for displaying HTML in a widget.

---

### Post by Horizon on 2006-06-03
Really? I thought it was because the azureus package in the repos needs the gnu interpreter for java (gij). Now that i think about it your reason makes more sense...kind of?

If you want decent download speeds and a client that actually works you'll want to use the official azureus client with sun java. The azureus that is in the repos has really slow download speeds which fluctuate from  0 to around 20 (if you're lucky) continuously every couple of seconds. It's a pitty because it looks a hell of a lot better than the official client :sad:

---

### Post by nubbe on 2006-06-05
Thanks for the ideas

---

