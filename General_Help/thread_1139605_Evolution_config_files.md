---
title: "Evolution config files"
date: 2009-04-27
forum: General Help
---

### Post by Lerxst on 2009-04-27
After upgrading to Jaunty, my Evolution Exchange account has completely hit the ground with lost connection to the exchange backend errors.

No matter what I do it won't work, so I thought I'd completely wipe Evolution from my system and start from scratch.
I've backed up Evolution, renamed ~/.evolution to something else, yet when starting it up, it still has my Exchange and POP account data set up in preferences.

I tried MAPI instead of OWA (didn't work), and after this there's something going that makes Evolution take ages and ages to start up, and then even longer to scan the Exchange server mailboxes, so I need to get rid of absolutely everything.

Didn't stumble upon anything in .gnome2 or .gnome2_private, so where's the account information stored?

---

### Post by 666f6f on 2009-04-28
gconftool-2 --recursive-unset /apps/evolution

Found it in google cache: [http://209.85.229.132/search?q=cache:o2TlIT49MykJ:ubuntuforums.org/archive/index.php/t-16671.html](http://209.85.229.132/search?q=cache:o2TlIT49MykJ:ubuntuforums.org/archive/index.php/t-16671.html)

---

### Post by jrogers360 on 2012-04-01
Thank you so much for posting the fix 666f6f.  Super helpful.

---

