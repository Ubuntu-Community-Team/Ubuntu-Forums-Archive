---
title: "Gutsy slow DVD burning"
date: 2007-10-26
forum: Dell  Ubuntu Support
---

### Post by {spitFire} on 2007-10-26
I'm running Gutsy on Dell E1505 and I can't burn any DVD's past 2.5x speed! When I try to burn using windows unfortunately it burns at 8x!!! None of the software on Ubuntu would burn at that speed! Is there  a fix to this problem? My DVD Drive model: TSSCorp DVD+-RW TS-L632D

---

### Post by Giggity on 2007-11-04
I'm having a similar DVD burning problem in Gutsy.  Back in Feisty, DVDs burned at maximum speed.

Since upgrading, about a third of the way through a DVD, the burning will slow down to some significantly level (11:13 for a 4200MB DVD+R that took ~6 minutes in Feisty), and go that slow until it's finished.  This problem existed in Dapper and Edgy, and I thought Feisty had fixed it for good, but Gutsy brought it back.

I'll try switching back to Feisty, since none of the new features of Gutsy actually benefit me (my computer is over a year old now).  I'll let you know how that works.

Using LITE-ON DVDRW SHW-160P6S as reported by Gutsy's Device Manager

**UPDATE:**  I realized after reinstalling Feisty and getting a ton of errors that I had forgotten to remove all of the .hidden files and folders in my /home directory, which I kept the same during the upgrade to Gutsy.  I'm guessing that some of the settings files therein were messing with some applications in Gutsy.  After removing them and doing a clean install of Gutsy, I'm able to burn a 4200MB disc in just over 6 minutes again.  I'll post again if this problem rears its head again.  Wow.  I really used the word "again" a lot in that post.

---

