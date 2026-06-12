---
title: "laptop freezes alot in xubuntu, need help logging"
date: 2008-03-16
forum: Desktop Environments
---

### Post by oddworld on 2008-03-16
I have a really old laptop running xubuntu, and it freezes a whole lot.
I need help finding the root of this problem.
It can be just sitting there idle after logging in and it will lock up.
CRTL ALT F2 does not do anything. CTRL ALT BACKSPACE will not do anything.
It is completely locked up.
Any ideas?

---

### Post by overdrank on 2008-03-16
> **oddworld said:**
> I have a really old laptop running xubuntu, and it freezes a whole lot.
I need help finding the root of this problem.
It can be just sitting there idle after logging in and it will lock up.
CRTL ALT F2 does not do anything. CTRL ALT BACKSPACE will not do anything.
It is completely locked up.
Any ideas?

HI and what are the specs on the system and what version of Xubuntu are you using, Gutsy, Feisty?

---

### Post by oddworld on 2008-03-16
Old Fujitsu laptop about 1.6 ghz, 512 megs ram, 20 gig Hitachi HDD.
Xubuntu 7.10

---

### Post by Darkhack on 2008-03-17
sudo apt-get remove powernowd

I'm on a desktop, but removing it has fixed all my lock ups.  I recommend you at least try it.  If it doesn't stop the lock ups then you can reinstall it.

sudo apt-get install powernowd

---

### Post by oddworld on 2008-03-17
That didn't work, I think its something to do with the hard drive.
Any way to know for sure?

---

### Post by Jouke74 on 2008-03-17
Try to run from a live-cd for a while? That way you won't use your harddrive.

Also test the memory of the laptop with memtest.

---

### Post by oddworld on 2008-03-17
I did memtest, no errors.

---

