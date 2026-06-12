---
title: "MP-BIOS Bug: 8254 timer not connected..."
date: 2009-04-15
forum: General Help
---

### Post by sadicote on 2009-04-15
I am very sorry, i know this has been posted and commented on a million times..i have no idea what 8254 timer is and do not notice that my computer is any the worse for this, still, i have to say this; the noapic workaround is not a solution, disabling the Apic support in the BIOS is not a solution..is this a problem that i should be concerned about, and, is there a real solution for this?

---

### Post by cariboo on 2009-04-16
I have had that error for a couple of years, even after a BIOS update it didn't go away, so now I just keep on ignoring it. 

I have corresponded with one of the kernel developers about the problem, he said it is up to the motherboard manufacturers to fix the problem.

Jim

---

### Post by sadicote on 2009-04-16
...but this has recurred only after my latest reinstall and re-upgrade! It did stop at some stage before that..if only i could duplicate, drat...

---

### Post by Ericyzfr1 on 2009-04-16
> **cariboo907 said:**
> I have had that error for a couple of years, even after a BIOS update it didn't go away, so now I just keep on ignoring it. 

I have corresponded with one of the kernel developers about the problem, he said it is up to the motherboard manufacturers to fix the problem.

Jim

This is not entirely correct, at least not in every case as this issue appeared on my wife's laptop (Toshiba) with 8.10. I went back and forth with fresh install of 8.04 and 8.10 to confirm the problem. The only way around it that I found was to upgrade from 8.04 to 8.10 and select the older kernel on the list as default.

---

### Post by sadicote on 2009-04-16
> **Ericyzfr1 said:**
> This is not entirely correct, at least not in every case as this issue appeared on my wife's laptop (Toshiba) with 8.10. I went back and forth with fresh install of 8.04 and 8.10 to confirm the problem. The only way around it that I found was to upgrade from 8.04 to 8.10 and select the older kernel on the list as default.
That is exactly what i am saying, the bug/whatever behaves as if it is has a mind of it's own! I have upgraded from Intrepid to Jaunty twice. With my first fresh install of Intrepid, this 'bug' got 'cured' by means which, as i have said before, i've no way of duplicating...

---

