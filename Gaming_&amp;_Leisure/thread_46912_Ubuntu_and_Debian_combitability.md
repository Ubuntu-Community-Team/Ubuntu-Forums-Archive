---
title: "Ubuntu and Debian combitability"
date: 2005-07-06
forum: Gaming &amp; Leisure
---

### Post by Turk on 2005-07-06
I wanted to install Flightgear, but some new dependings were needed, but these aren't in Synaptec, and the synaptec version is like : 5ubuntu1.0(something like that), if I update to a non ubuntu type, will this be allowed and will the os give some problems, I am now on Warthy, but I will update soon.

And are all the .deb packs compitable, so I add the deb rep of the debian site to synaptec?

---

### Post by bunced on 2005-07-07
Of course all Debian packages are compliant

INSTALL AT WILL!

David

---

### Post by Takis on 2005-07-08
[QUOTE=bunced]Of course all Debian packages are compliant

INSTALL AT WILL!

David[/QUOTE]
Uhhhhhhhhhhm no - they're not.

In most cases, yes, you should be okay, but there is a chance something will come along and break things.

Turk your best bet (if you can be bothered) is to get the source for each dependency, compile it yourself and then install your game. This may be overkill, this may save your system. Word of advice though: don't add the debian repositories to synaptic permanently.

---

### Post by DJ_Max on 2005-07-09
Takis is right. Debian packages and Ubuntu packages just use the same format(.deb), but they are compiled, and made differently, against different libraries and such. This has been discussed numerous times. You will run into problems using packages made for another distribution.

---

