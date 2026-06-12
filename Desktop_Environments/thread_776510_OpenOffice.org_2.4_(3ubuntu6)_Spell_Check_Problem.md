---
title: "OpenOffice.org 2.4 (3ubuntu6) Spell Check Problem"
date: 2008-04-30
forum: Desktop Environments
---

### Post by mogwai on 2008-04-30
I am having trouble with the spell check on openoffice.org. I go into Tools->Options->Language Settings->Language and choose English (UK).
The first thing I notice is that there is no blue tick beside ANY of the languages like there used to be.
I then spell check my document with a known spelling error (dokkummantetiann: supposed to be documentation) and go spell check (F7).
I asks me if I want to start from the beginning of the document. I click YES. It says "The spelling check is complete". I click on OK. It closes the spell check window.
It has _NOT_ picked up my spelling error. :(

Another thing I noticed is the Spell Check window has a "Dictionary Language" with a blank drop-down box beside it, but I can't work out how to change it as I cannot access the window (Brings up window, Pops up dialog "Do want to start from beginning of document", click YES (no closes the dialog and window), it pops up another dialog "Spelling check complete", Click ok, closes dialog and spellcheck window.)

I have read bug reports of similar problems, but none have been *exactly* the same as my problem and have been fixed. :confused:

If I don't find a resolution soon, I will submit a bug report. But any Confirmations, Work-Arounds, Comments, Questions, etc. are welcome.

mogwai

---

### Post by mogwai on 2008-04-30
NOTE: Running Hardy Heron (8.04), upgraded from 8.04 beta. Have checked and installed latest updates.

---

### Post by mogwai on 2008-04-30
Found a solution to my problem here:
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/65318](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/65318)
Installed myspell-en-gb and was away.
Spelling window now has "[tick] English (UK)" in the 'Dictionary Language' box.

---

### Post by rafttrip on 2008-11-26
[http://www.oooforum.org/forum/viewtopic.phtml?t=50862](http://www.oooforum.org/forum/viewtopic.phtml?t=50862)

This link was very helpful for me.:)

note: F11 did not work for me but at the top right of the 2nd tool bar there an icon that looks like a hand clicking on a button in a grid of 9 squares, this is the styles dialog that the article in the link is talking about.

For me the problem seams to be that the system thinks that i am in Canada but there is no Canadaian dictionary installed.

---

### Post by Hagar Delest on 2008-11-27
The link above is deprecated, see here for the new version that applies to 3.0 also: [[Tutorial] Spell check and Language configuration](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=67).

F11 is the Stylist, can be also opened with menu Format>Styles and formatting.

---

