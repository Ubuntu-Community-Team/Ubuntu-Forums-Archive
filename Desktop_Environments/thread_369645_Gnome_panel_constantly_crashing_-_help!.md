---
title: "Gnome panel constantly crashing - help!"
date: 2007-02-24
forum: Desktop Environments
---

### Post by epimer on 2007-02-24
Just a few hours ago, my gnome panel started crashing whenever I hit my main menu button. I tried to make things easier by adding the default menu object to the panel, and now it simply crashes whenever it relaunches itself! It's made the system pretty much unusable, and I don't know how to fix it.

The bug report is attached.

---

### Post by fazavon on 2007-02-24
Which flavor are you using? 6.06, 6.10, 7.04 Alpha?

---

### Post by Nersis on 2007-02-24
I had the same problem and i fixed it typing

rm ~/.recently-used.xbel

restart the computer and i works ok again

---

### Post by epimer on 2007-02-25
Thanks, Nersis! Did that and it worked a treat.

fazavon, 6.10, but I don't suppose it matters any more :)

Thanks guys!

---

### Post by fazavon on 2007-02-28
I have the 7.04 in VMWARE and my panel keeps doing that too. but ill try the fix and let you know how it goes

---

### Post by RacerII on 2007-03-13
> **Nersis said:**
> I had the same problem and i fixed it typing

rm ~/.recently-used.xbel

restart the computer and i works ok again

Ty , you just helped me out.

I tied to unpack an iso and this started happening , but its solved now.

---

### Post by LeSkip on 2007-04-21
Had same problem after upgrading to feisty, and this fixed it! Thanks!

---

