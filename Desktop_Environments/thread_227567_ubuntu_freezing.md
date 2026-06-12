---
title: "ubuntu freezing"
date: 2006-08-01
forum: Desktop Environments
---

### Post by thatcoolrushguy on 2006-08-01
I'm experiencing frequent freezing of Ubuntu 6.06. It happens at least once daily, and freezes to where I can't even move the mouse. It appears to happen randomly and I can't determine if any program in particular is causing it. Is it a corrupted installation? How do I fix this?

Thanks :D

---

### Post by dtfinch on 2006-08-03
If you're seeing clock drift as well, you might have an APIC problem, which wouldn't affect most older distros. It's a longshot, but if this is the problem, booting with the noapic kernel option would fix it.

---

