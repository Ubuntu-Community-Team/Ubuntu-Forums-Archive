---
title: "get the clock back"
date: 2015-09-27
forum: Desktop Environments
---

### Post by Skaperen on 2015-09-27
running unity on 14.04.3 LTS:

near the upper right corner the time used to be shown ... **how do i get it back?**

it _disappeared_ for most users but not all.:mad:

---

### Post by grahammechanical on 2015-09-27
Have you tried

System Settings>Time & Date>Clock tab>Show a clock in the menu bar = a tick?

Regards.

---

### Post by Skaperen on 2015-09-30
> **grahammechanical said:**
> Have you tried

System Settings>Time & Date>Clock tab>Show a clock in the menu bar = a tick?

Regards.
_thanks!_   i kept right-clicking the menu to get the properties _submenu_ but no such luck (all there is, is *Minimize, Unmaximize, Move Resize, Always On Top,* and *Close*).  GUI is so unpredictable.

but, that does not get the clock back for users that have it missing.  it was already checked so i clicked it off then back on and still no clock.

---

### Post by howefield on 2015-09-30
While since I've seen this issue, but if I recall correctly, this worked.

```
killall unity-panel-service
```

---

### Post by Skaperen on 2015-09-30
> **howefield said:**
> While since I've seen this issue, but if I recall correctly, this worked.

```
killall unity-panel-service
```

still no clock.

i also logged out the user and logged back in and still no clock.

---

### Post by Skaperen on 2015-09-30
i found the problem and got the clock back.

the problem is that _System Settings>Time & Date>Clock tab>Weekday_ and _System Settings>Time & Date>Clock tab>Date and month_ both cause the clock to go away (probably crashes).  unsetting both of them gets the clock back.

looks like a bug in the clock.  can someone running 14.04 LTS try it?  either *one* of those options kills it for me.

---

### Post by Skaperen on 2015-10-01
anyone running Trusty Tahr 14.04 LTS?

---

