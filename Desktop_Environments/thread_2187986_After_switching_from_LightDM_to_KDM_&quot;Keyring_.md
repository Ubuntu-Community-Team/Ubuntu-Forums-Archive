---
title: "After switching from LightDM to KDM: &quot;Keyring did not get unlocked&quot;"
date: 2013-11-14
forum: Desktop Environments
---

### Post by W-Unit on 2013-11-14
Hi there. I recently changed my display manager to KDM from LightDM; everything is fine except, when I log in, I get a dialog that says that the "login keyring did not get unlocked" when I logged on, and I have to enter my password again.

This is just a little bit annoying...

In [a similar thread](http://ubuntuforums.org/showthread.php?t=1448143) somebody advised editing /etc/pam.d/kdm however the fix described therein seems sketchy. Also since it's such an old thread I'm wondering if any better fixes for this issue have come along.

Thank you guys! :)

---

### Post by public3 on 2013-11-19
You're probably missing a package that takes care of this. Is there any reason you didn't just use one of light-dm's KDE themes?

---

