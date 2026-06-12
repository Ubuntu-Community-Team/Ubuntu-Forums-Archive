---
title: "BlackBox - toolbar clock"
date: 2006-08-01
forum: Desktop Environments
---

### Post by shotomonk on 2006-08-01
Hi All,

I'm a relatively new to Ubuntu, I have installed Ubuntu 5.10 and have been trying out various X Windows Managers to find out which one I prefer, which I've found to be BlackBox. But for some reason the clock on the toolbar is wrong by exactly 12 hours, when I do a date command I get the correct time, but the clock on the toolbar doesn't display the same time. I can't see any clock configuration tool of the menu display, anyone have any ideas how I can resolve this?

Any help is much appreciated!

Cheers

Shotomonk

---

### Post by ardchoille on 2006-08-01
What happens if you set the time with:
```

gksu time-admin

```

Does that help?

---

### Post by Tomosaur on 2006-08-01
Uhm. Are you sure it's not just set to 12 hour format?

---

### Post by shotomonk on 2006-08-01
Ardchoille - I have run 'gksu time-admin' and that displays the correct time.  But thanks for the recommendation.

Tomosaur - I thought that originally but I wouldn't expect it to displayed as 07:06 for example if it was in 12-hr format.

---

### Post by Tomosaur on 2006-08-01
Why not? There's still 12 hours in a 12 hour format, from 00:00 up to 12:59.

---

### Post by Riverside on 2006-08-01
> **shotomonk said:**
> Tomosaur - I thought that originally but I wouldn't expect it to displayed as 07:06 for example if it was in 12-hr format.I suspect that 12-hr format is the issue, since that is the Blackbox default.

Try editing ~/.blackboxrc, editing the relevant line to read:

session.screen0.strftimeFormat: %a %d/%m/%y %H:%M

You will find, I hope, that this resolves the issue.

---

