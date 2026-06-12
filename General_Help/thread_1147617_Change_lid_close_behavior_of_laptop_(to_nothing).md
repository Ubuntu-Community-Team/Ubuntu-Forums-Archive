---
title: "Change lid close behavior of laptop (to nothing)"
date: 2009-05-03
forum: General Help
---

### Post by tnek on 2009-05-03
Hi,

At the moment, I guess by default, the system goes into the Hibernate state when I close the lid of my laptop.

Is it possible to turn off this behavior? Or make it into something else?

[B]I would like to do nothing at all when the lid is closed.
[/B]
But it would be interesting to know if and how I could turn it into some other functionality (say by executing a script when the lid is closed).

---

### Post by drs305 on 2009-05-03
System, Preferences, Power Management.

---

### Post by tnek on 2009-05-04
I'm actually running Xubuntu and don't have that option. Is there another way? (Maybe more low-level, like editing a script somewhere.)

---

### Post by ddrichardson on 2009-05-04
/etc/acpi/events/lidbtn is called on closing the lid but Ubuntu has an oddly complicated set of scripts.

---

### Post by ddrichardson on 2009-05-04
You could comment out the call to lid.sh and add```

pm-suspend
```

---

### Post by tnek on 2009-05-05
Great answer! Thank you!

I just commented out both event and action (I had one of each) in lidbtn and closed it, nothing happened just as I like it. :-)

I didn't put in any pm-suspend in there. I guess it puts the machine in suspend mode? Anyway, I want to continue working using an external keyboard and mouse, having the lid closed. And I'm able to do that now, so I'm satisfied.

---

### Post by ddrichardson on 2009-05-05
Glad it worked for you.

---

