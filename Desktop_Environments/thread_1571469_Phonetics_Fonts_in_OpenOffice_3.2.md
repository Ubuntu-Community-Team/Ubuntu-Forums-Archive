---
title: "Phonetics Fonts in OpenOffice 3.2"
date: 2010-09-09
forum: Desktop Environments
---

### Post by Sigma1 on 2010-09-09
Hello,
I use OpenOffice 3.2 and Ubuntu 10.04. Before, with OpenOffice 2.4 and Ubuntu 8.04 the phonetics font Ipa-samd Uclphon1 SILDoulosL (downloadable free here: [http://www.phon.ucl.ac.uk/shop/fonts.php](http://www.phon.ucl.ac.uk/shop/fonts.php)) worked perfectly. Now it doesn't.
The font appears in the list of possible fonts and is the right place, /usr/share/fonts but doesn't display properly: a replacement font is used. When I choose Insert / Special characters, I get the desired result however. I think it's an OpenOffice problem really, as Gedit and Abiword display the font fine.
Any help much appreciated!

---

### Post by Hagar Delest on 2010-09-09
Perhaps you can try the vanilla version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Sigma1 on 2010-09-10
Hello,
Thanks for the suggestion. I gave it a go, but it still doesn't display the phonetics font correctly. I think it OpenOffice must be looking for the font in the wrong place, hence the replacement, but even when I delete the .openoffice config folder in my home directory, the problem persists. It's a real headache since I teach phonetics and I've a load of material which is currently unusable!
Thanks for your help!

---

### Post by Hagar Delest on 2010-09-10
Try to put the fonts in your ~/.fonts folder.

---

### Post by Sigma1 on 2010-09-10
Thanks, ~/.fonts is where Lucid puts fonts when you click on the automatic install button, I think. I've tried that, as well as changing the permissions variously, but with no success.
I've been reporting progress on a French forum, here: [http://user.services.openoffice.org/fr/forum/viewtopic.php?f=13&t=24358](http://user.services.openoffice.org/fr/forum/viewtopic.php?f=13&t=24358) I've at least succeeded in installing 2.4 alongside 3.2 and so I can now work on my original files using OOo. Otherwise I made a bug report here: [http://www.openoffice.org/issues/show_bug.cgi?id=114440](http://www.openoffice.org/issues/show_bug.cgi?id=114440) which might bear fruit, I hope.
Thanks again for the suggestions.

---

### Post by Hagar Delest on 2010-09-10
A bug indeed. I have installed the font, works in Mousepad but doesn't in OOo 3.2.1 (Sun version) on xubuntu 10.04.

---

### Post by Sigma1 on 2010-09-10
Thanks for testing this: it's nice to know I'm not the only one!

---

### Post by ZaphodFJ on 2010-09-10
Check here: [http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&id=OOo_20_graphite](http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&id=OOo_20_graphite)

OOO 3.2 was the first to incorporate the SIL 'Graphite' rendering engine in the main project.  Until then there was a SIL fork, from 2.0 onwards that used it while it was in development.  It might be worth checking whether SIL version 2.4 has the problem - to at least know if Graphite has a knock-on bug.

Surprising that a version of OOO that SIL had a hand in isn't displaying their own fonts - I'd have thought this would have been checked.  I've used it with W.African reading primers (Go-oo on Win Vista and Sun OO in XP) and it seems to be fine.  I'd be interested in the outcome of this!

---

### Post by Sigma1 on 2010-09-11
Thanks for the suggestion. I tried downloading the graphite extension and tweaking the settings on and off, but with no difference to the display. It's probably fair to say that the font I use is far from being the most complete phonetics font available, but it is easy to use and to type with, since the English phonemes are all accessible via keyboard combinations. Otherwise there are indeed a number of SIL developed fonts which do work nicely with OOo and graphite rendering.
Since the problems began I have installed OOo 2.4 alongside 3.2, and 2.4 renders fine, as before. See screenshot below:

[IMG]http://straw.blog.free.fr/public/Capture-4.jpg[/IMG]

---

### Post by Sigma1 on 2010-09-14
Looks like the issue has now found an answer, which is impressive. Here is the follow-up to the bug report:
> When they display fine when you use insert-char but not when you type them as "normal" alphanumeric 
keys this indicates that symbol-aliasing is not activated. This reminds me of issue 112379 (fixed in 
OOO330). The symptoms were that some symbol fonts did not get recognized as such and so the features 
symbol-preview and symbol-aliasing didn't get enabled.

 Please check with OOo33 beta or newer.

*** This issue has been marked as a duplicate of 112379 ***
I've tested it with the development version of OOo 3.3 and it now displays correctly, as with the older version 2.4, see screenshot below:
[IMG]http://straw.blog.free.fr/public/Capture5.png[/IMG]
Many thanks to the community for your help!

---

