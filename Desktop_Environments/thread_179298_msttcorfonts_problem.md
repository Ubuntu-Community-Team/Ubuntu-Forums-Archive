---
title: "msttcorfonts problem"
date: 2006-05-19
forum: Desktop Environments
---

### Post by dphipps on 2006-05-19
I have installed msttcorfonts with Automatix but they do not seem to work.  The fonts do not show up in the font list under firefox and when I get black spaces where words should be on some websights (like goowy).

---

### Post by aysiu on 2006-05-19
Just to make sure there wasn't some kind of glitch with Automatix's interface, can you paste this command into the terminal? ```
sudo apt-get update && sudo apt-get install msttcorefonts
``` If it is indeed installed, you should get a message saying it's already the newest version. If not, it'll install the fonts for you.

---

### Post by dphipps on 2006-05-19
I tried that and it says that I have the newest version.  Earlyer I also tried reinstalling it with Synaptic but this did not seem to help.

---

### Post by dphipps on 2006-05-20
I looked into this and I think that maybe msttcorfonts are working.  They just don't seem to be working on the page that I need them to (goowy.com).  Could this be a problem with flash?

---

### Post by aysiu on 2006-05-20
[QUOTE=dphipps]I looked into this and I think that maybe msttcorfonts are working.  They just don't seem to be working on the page that I need them to (goowy.com).  Could this be a problem with flash?[/QUOTE] I don't know. 

This is a shot in the dark, but maybe it's a corrupt profile? [Try this](http://www.ubuntuforums.org/showthread.php?t=103930) and see if that's the problem.

---

### Post by dphipps on 2006-05-20
I do not think that it is a problem with Firefox because the same thing happens when I use Opera.

My problem seems to be the same as a Bugzilla Bug 11851.

[http://bugzilla.ubuntu.com/show_bug.cgi?id=11851]("http://bugzilla.ubuntu.com/show_bug.cgi?id=11851")

I am still not sure what to do about it through.

---

