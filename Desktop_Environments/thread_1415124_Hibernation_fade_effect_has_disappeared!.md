---
title: "Hibernation fade effect has disappeared!"
date: 2010-02-24
forum: Desktop Environments
---

### Post by mgough85 on 2010-02-24
I remember when I first installed Ubuntu 9.10 on my computer that there used to be a neat screen effect when entering hibernation where it would fade to black.  It has stopped that, possibly after I ran the system updater.  How can I restore this?

---

### Post by Hero of Time on 2010-02-25
It depends where you picked your hibernate option, because the screensaver can be responsible for that. If you set it to fade to black and activate the screensaver when it's told to lock, and the hibernate option activates the lock mechanism, then it would fade.

If that isn't it, I'm afraid you have to dig into the system to find out what scripts it's running before going to hibernate and what changes were made to the corresponding packages. I'd check the acpi-support or other related packages first.

---

### Post by mgough85 on 2010-02-25
Thank you,
I disabled screensavers in the startup programs, I'll try fixing that.

update: that was it

---

