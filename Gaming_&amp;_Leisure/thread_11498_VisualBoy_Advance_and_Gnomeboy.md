---
title: "VisualBoy Advance and Gnomeboy"
date: 2005-01-17
forum: Gaming &amp; Leisure
---

### Post by puzzledm on 2005-01-17
I installed VisualBoyAdvance via ./configure, make and sudo make install (I forgotten what you call that method!) and then installed GnomeBoyAdvance (which is the frontend for the above) via a .deb file and dpkg ...

However during installation it said visual boy advance was required and is therefore not seeing that I have installed it.  How do I make the two play nicely together?

---

### Post by nocturn on 2005-01-17
[QUOTE=puzzledm]I installed VisualBoyAdvance via ./configure, make and sudo make install (I forgotten what you call that method!) and then installed GnomeBoyAdvance (which is the frontend for the above) via a .deb file and dpkg ...

However during installation it said visual boy advance was required and is therefore not seeing that I have installed it.  How do I make the two play nicely together?[/QUOTE]

You will need to either install both from .deb, or neither.  So compiling GnomeBoyAdvance will help.

You could also look at checkinstall to create .deb packages from make install.

---

