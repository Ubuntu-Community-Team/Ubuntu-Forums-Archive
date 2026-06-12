---
title: "Dell E6520, 2 external monitor problems."
date: 2011-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jasolruser on 2011-07-22
Hi,

I have a Dell E6520, with an install of Ubuntu 10.04.  It has a docking station, external keyboard, mouse, and 2 monitors.

The problem I have is this:  

I cannot get Ubuntu to detect the monitors.  Instead, the same image is displayed on BOTH monitors, presumably with the system believing there is only one monitor present.

Any thoughts?

Jim

---

### Post by w15p on 2011-10-10
Have you tried ```
disper -l
```?

This will easily let you know if the system 'sees' the monitors.

Read up on disper - it's great for switching modes (docked/undocked)

hth.

---

