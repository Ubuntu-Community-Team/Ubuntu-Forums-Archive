---
title: "Reverting from Gnome3 back to Unity"
date: 2011-06-30
forum: Desktop Environments
---

### Post by peterdm on 2011-06-30
I reverted back from Gnome3 to Unity using ppa-purge, but now I have 2 annoying issues:

[LIST]
[*]The launcher reverts back to its default after login/logout. Any extra items I "Keep in launcher" are gone.
[*]The clock is stuck in 12h mode and it doesn't take any new settings. 24h clock, showing seconds etc. all fail.
[/LIST]

I have 2 different systems affected, one 64-bit and one 32-bit (pae kernel).

Any ideas on how to fix this?

---

### Post by wildmanne39 on 2011-06-30
> **peterdm said:**
> I reverted back from Gnome3 to Unity using ppa-purge, but now I have 2 annoying issues:

[LIST]
[*]The launcher reverts back to its default after login/logout. Any extra items I "Keep in launcher" are gone.
[*]The clock is stuck in 12h mode and it doesn't take any new settings. 24h clock, showing seconds etc. all fail.
[/LIST]

I have 2 different systems affected, one 64-bit and one 32-bit (pae kernel).

Any ideas on how to fix this?Hi, look here to fix your launcher problem.
[http://ubuntuforums.org/showthread.php?t=1787391](http://ubuntuforums.org/showthread.php?t=1787391)

---

### Post by peterdm on 2011-07-04
Reinstalling libdconf0 worked! Thanks!

---

