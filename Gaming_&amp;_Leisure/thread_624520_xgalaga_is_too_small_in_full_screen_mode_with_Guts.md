---
title: "xgalaga is too small in full screen mode with Gutsy"
date: 2007-11-27
forum: Gaming &amp; Leisure
---

### Post by grahams on 2007-11-27
After upgrading to Gutsy Xgalaga is tiny and unplayable in full screen mode. 

Anyone know a way to fix this (apart from re installing feisty)?

I also can not change the resolution on my laptop screen from the native 1400x1050, (could on feisty). My guess is that this is related.

---

### Post by grahams on 2007-11-28
bump

---

### Post by grahams on 2007-12-04
This is somehow related to my old Compaq n610 laptop as I installed xgalaga on a T60 laptop with Gutsy and all is well.

Reinstalled Feisty on the n610, everything is good again.

---

### Post by grahams on 2008-02-27
Same issue with Hardy live cd. Seems old ATI controller isn't recognized correctly.

---

### Post by grahams on 2008-04-15
At the risk of talking to myself, does anyone have a workaround or fix for this?

---

### Post by Cappy on 2008-04-15
So basically your resolution is wrong? That's really easy to fix, look here:
[http://ubuntuforums.org/showpost.php?p=469846&postcount=3](http://ubuntuforums.org/showpost.php?p=469846&postcount=3)

Just put the correct resolution on the Modes line in front of the others and with parenthesis.

---

### Post by grahams on 2008-05-03
Any edits in xorg.conf are ignored and only the native res on the laptop screen is available. Same deal on Hardy I'm afraid. Logged as a bug @

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/160871](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/160871)

---

### Post by grahams on 2008-05-07
Solved

add the following to xorg.conf in the device section

Option "NoDDC"

---

