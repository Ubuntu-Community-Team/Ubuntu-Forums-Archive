---
title: "How do i kill the screensaver?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by kitten on 2006-06-10
guys,

   under Breezy i had the option to stop the screensaver from running completely, this doesn't seem to be available in Dapper.

   i hate screensavers, i want to deep six them, and no, a blank screen is *not* an option ... i just want the fscking thing _gone_!!!

god protect me from desktop crapulence.

---

### Post by john280z on 2006-06-10
kitten,

   Open a terminal and type "xscreensaver-demo". This will open a gui with "none" as one of the options.
   
johnm

---

### Post by steve.horsley on 2006-06-10
System->Preferences->Screensaver,
un-check Activate screensaver...
Click Close

---

### Post by kitten on 2006-06-20
thanks boys, but i'm not actually an idiot, so i tried those *before* asking for help.

the answer turned out to be a kernel bug that triggered the power management.

the latest kernel upgrade seems to have fixed it.

---

### Post by kitten on 2006-08-04
Actually, it's:

> Open a terminal and type "sudo xscreensaver-demo". This will open a gui with "none" as one of the options.


note the "sudo" ... necessary so that the screensaver & power management are switched off at the root level, not just the account level.

---

