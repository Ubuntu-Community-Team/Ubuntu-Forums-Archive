---
title: "What screensavers are included in Ubuntu minimal &amp; how do I disable all of them?"
date: 2010-11-05
forum: Desktop Environments
---

### Post by phile on 2010-11-05
I'm setting up a kiosk application based on the Ubuntu minimal installation. It is vital that the screen is on all the time but I'm finding that, despite disabling power management and apparently having no Gnome screensavers installed, the screen blanks (shuts down - LED on the front goes from green to orange, if you see what I mean) after 10 mins of inactivity.

Can anyone suggest what might be causing the screen to blank and how I can stop it?

Thanks,

Phil

---

### Post by sisco311 on 2010-11-05
Check the X server's DPMS settings:
```
xset q
```

---

### Post by phile on 2010-11-05
Aha! That's the badger!

Thanks sisco311. Problem solved.

P.

---

### Post by sisco311 on 2010-11-05
You're welcome!

Don't forget to mark this thread as [SOLVED]. At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" menu, then "Mark this thread as Solved".

---

