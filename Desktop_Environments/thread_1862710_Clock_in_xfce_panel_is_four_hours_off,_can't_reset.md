---
title: "Clock in xfce panel is four hours off, can't reset it."
date: 2011-10-17
forum: Desktop Environments
---

### Post by MarjaE on 2011-10-17
I've reset the clock in the accessories, but that hasn't changed the clock in the panel.

---

### Post by gsmanners on 2011-10-17
Have you set your Time zone? That's in the Time and Date Settings.

---

### Post by MarjaE on 2011-10-17
> **gsmanners said:**
> Have you set your Time zone? That's in the Time and Date Settings.

Yes, but the clock's still off.

---

### Post by marinara on 2011-10-20
The clock in the panel is called 'orage'
it has it's own time zone settings.
so you have to double-click the clock, set time zone.

IMHO, ubuntu is too damn hard.

---

### Post by Rodney9 on 2011-10-21
Under 'System' in 'Time and Date' click the lock to make changes and click 'configuration' and select 'Internet Servers', select one or more.

The Internet servers will use an atomic clock, precise to milliseconds. This should override any bios or battery problems.

---

