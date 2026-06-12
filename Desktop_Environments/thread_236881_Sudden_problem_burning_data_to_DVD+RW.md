---
title: "Sudden problem burning data to DVD+RW"
date: 2006-08-15
forum: Desktop Environments
---

### Post by mchatel on 2006-08-15
Hey everyone.
I just all of a sudden started having trouble, burning data to DVD+RW discs, and was wondering if anyone else has encountered this same problem?

About once a week... maybe every couple of weeks, I back-up my Ubuntu system by creating a .tar file, which I then proceed to burn to a DVD+RW disc, as a backup.  This has worked perfectly for me since my Hoary days.  For some reason, all of a sudden, I can't do this anymore.

I always use the built-in CD/DVD creation tool through Nautilus to do this.  When I try to burn the DVD+RW disc, instead of trying to make the image like it always did in the past, it seems to very quickly go to the "this disc already has info on it" step, and asks me if I want to "...erase this disc?".  So I say yes...but the disc doesn't actually erase.  Almost immediately, it goes to the "finishing writing" step, and it thinks it burned the disc, except that the disc has nothing on it.

I don't know what is causing this?  I thought that maybe my DVD+RW disc was just going bad, after so many uses, so I tried some new ones too, but the same thing happens.  

I also tried doing this same task under K3B, and it doesn't work either.  Did a recent system update break the DVD burning in Dapper?

---

### Post by mchatel on 2006-08-15
Sorry.  This turned out to be a filesize issue.  Once I shrunk the file a bit more, it burned okay.

So, I'm guessing the filesize was too big, and that there was just a bug in the Gnome GUI dialogs for the CD/DVD Creator, to make it act like it did, instead of giving error messages or complaining.

I may purposely step through this process again, using a larger file, to see if it is indeed a bug.  Should probably be documented or reported, if so.

But first, I gotta finish my backup.  :)  I'll feel safer then.  :D

---

