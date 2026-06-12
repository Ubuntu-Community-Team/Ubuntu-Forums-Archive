---
title: "[SOLVED] Tracker strange behaviour"
date: 2008-12-09
forum: General Help
---

### Post by FokkerCharlie on 2008-12-09
Hello!

Perhaps someone could shed some light on what I am experiencing in Tracker.  I use the utility from the deskbar-applet, which is very handy.  Except that it seems very hit-and-miss.

For instance, I can type in part of a filename, and as often as not, the file won't be found.  Eg- I have a file in a sub-sub folder of my home folder called 'Memberships.ods'.  If I type in 'Memberships', no file is found.  In another sub-sub folder, I have several files where the name includes 'Roster' (followed by a date); typing roster into tracker only turns up one of these files.

I also have a file somewhere else named 'Welcome to Ubuntu.pdf'.  Typing in 'Welcom' works in tracker, but typing 'Welcome' does not!

What am I missing?  Is this a bug?  Or am I being a dimwit?  Perhaps a matter of getting tracker to re-scan everything or something...

Please advise!
Charlie

---

### Post by ajgreeny on 2008-12-09
There was a time in a previous ubuntu where I had the same problem, (I'm now on hardy not intrepid) and I overcame the problem by stopping the daemon and rescanning with
```
killall trackerd
trackerd -v 2 -R
```From then on all was well with the utility.  I have no idea why it happens, but give that solution a try; even if it doesn't work, it will do no harm.  Scanning can take a long time and use resources if you are trying to work on the computer, so perhaps try it overnight, not when you are working on the machine.

---

### Post by FokkerCharlie on 2008-12-10
Well, that seemed to fix it alright- thanks!

Perhaps it got interrupted the first time it tried to index everything, I don't know.  By the way- is there a GUI equivalent of the above commands?

Cheerio!
Charlie

---

### Post by ajgreeny on 2008-12-10
I'm afraid I have no idea about that, but it is so easy anyway, that I've never even looked for a gui equivqlent.

---

### Post by philinux on 2008-12-10
killall trackerd
trackerd -v 2 -R

Nice one. It threw some errors up about a database not being there and created it. This is a fresh install form about 3 weeks ago. I reckon trackerd is still bleeding edge.

---

