---
title: "Dual monitors with Compiz fusion on ATI cards"
date: 2007-08-25
forum: Desktop Effects &amp; Customization
---

### Post by Inquisitr on 2007-08-25
I recently got Compiz-fusion working on my ATI card.  I'm wondering if there is a way to make it also now work for my dual display.  It's a 2 headed video card and using the restricted ATI driver I could get dual display working, but since I switched to the open source driver with Compiz I can't find a way to get it to work.

The second monitor displays, just a clone of the first.

Any helps would be appreciated

---

### Post by synthaxx on 2007-08-25
I'm sorry to say it, but I've tried the same and semi-failed.


If you want to enable the second head in the open source driver, your best bet is to add the second display information in the device section of the first card.
<edit> [Here is the link to the information you want!]("https://help.ubuntu.com/community/RadeonDriver#head-93fc0a86162afbf71a5b84eff7da6c6a338656b1") Scroll down to the dual head configuration.</edit>


I've been an ATI customer since the Mach8/Rage era, but in a couple of weeks i'll be buying my first GeForce card. Their drivers suck THAT BAD.

---

### Post by Inquisitr on 2007-08-25
I tried editing my Xorg.conf with both MergedFB and Xinerama.

with Merged FB nothing happened, I editied, loged out and back in, and it was still cloned.

With Xinerama my mouse cursor disappeared.

I tried a fresh install of Ubuntu without Compiz fusion to see if the edits would work there, and they gave the same results.

---

### Post by Inquisitr on 2007-08-26
shameless bump.

Have a bet going with a friend as to who can get dual monitors working first, my geeky pride depends on it!

---

### Post by Mongo5000 on 2007-08-26
> **Inquisitr said:**
> shameless bump.

Have a bet going with a friend as to who can get dual monitors working first, my geeky pride depends on it!

Go get an nvidia card and you'll easily be first.  Install the card, boot up, enable restricted drivers, enable twinview, your done.

I spent weeks trying to get my ATI card to work properly.  Just could never get it right.  Went out and bought a nvidia card and had dual monitors with Beryl working in minutes.

---

### Post by Inquisitr on 2007-08-26
> **Mongo5000 said:**
> Go get an nvidia card and you'll easily be first.  Install the card, boot up, enable restricted drivers, enable twinview, your done.

I spent weeks trying to get my ATI card to work properly.  Just could never get it right.  Went out and bought a nvidia card and had dual monitors with Beryl working in minutes.


wish it was that easy, but cash is kinda an issue right now so I gotta make do with what I got.

---

### Post by pinoyskull on 2007-09-05
so...

somebody got this working on ATI card yet?

---

