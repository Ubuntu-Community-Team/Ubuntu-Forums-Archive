---
title: "Dell dimension 3000"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by Zeph2007 on 2007-07-01
Hi,,

After reinstalling windows xp on my computer nothing works properly, drivers are missing for the ethernet controller, and the display is stuck in a low resolution.

Will installing Ubuntu include all the necessary drivers so I can browse the Internet etc and ditch xp completely

---

### Post by evilghost on 2007-07-01
Yes.

It should use the i810 driver, you'll need to likely use the 915resolution package to get the correct resolution.  There's a ton of howto's for that.

---

### Post by Zeph2007 on 2007-07-01
cheers for that,,

it keeps freezing during installation with 7.04 so I'm downloading 6.06 to see if that works,,

---

### Post by evilghost on 2007-07-01
Try using the acpi=off or the noapic option.  Search the forum for more info about these options :)

---

