---
title: "kate settings don't save"
date: 2012-11-14
forum: Desktop Environments
---

### Post by dwlamb on 2012-11-14
I am using Ubuntu 12.04 with KDE added on.  I can not modify the settings for Kate and can't find a solution.

For some, this has been a challenge going back to the days of Hardy and was usually a permissions issue or fixed by deleting katerc and redoing the settings from scratch.  I have no permission issues in my Home folder and deleting katerc is not fixing the issue either.

An old fart with ailing eyesight, all I wish to do is increase the font size.  Can't get it to change for time I am working in Kate, never mind saving the changes.

---

### Post by gabrieldalrovere on 2013-07-14
This happened to me too. This is because the permissions of the **/home/****[COLOR=#006400]username[/COLOR]/.kde** are only for root. I decided this way:

**sudo chown   [COLOR=#006400]username[/COLOR]:[COLOR=#006400]username[/COLOR] /home/[COLOR=#006400]username[/COLOR]/.kde -R**


Hope that helps.

---

