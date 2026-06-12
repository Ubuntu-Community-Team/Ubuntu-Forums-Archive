---
title: "Gnome desktop refreshing and icons problems"
date: 2011-03-05
forum: Desktop Environments
---

### Post by whatsilenceknows on 2011-03-05
Hello,

I have a problem with Gnome desktop, since today's turning on  the computer. Basically, Ubuntu started with all the icons messed up, and I cannot 'organize' them as they were, because every time I refresh desktop - they mess up again to the 'standard' organization, in columns, from left to right. Plus, I'm unable to set method or organization  for directories ("by the name", "by  the size", "by the date of modification", et al.) because it immediately resets itself after I enter new directory and move back to the old directory again.
Also, the little 'symbols' that you can add to icons through the 'Properties' right-click menu won't show up anymore and are unable to turn on as well.
Any ideas where I should look for solution? I shall add that condition appeared after a hard-reset caused by shortage of electric current which happened right in spot when Gnome was loading desktop (after background showed up, and before icons showed up). Then - after next launch, computer acts as descirbed.

Thanks in advance!

PS
xsession-errors file shows problems with loading Metacity session file which doesn't exist. Could this be somehow helpful?

---

### Post by whatsilenceknows on 2011-03-05
Absolutely nothing?... :confused:

---

### Post by stoneage on 2011-03-05
I don't know what the problem is, or how to fix it, but you could try, next time you log in, choosing the 'Start new session' option. Maybe it will create the missing session file and your settings will persist.

---

### Post by Krytarik on 2011-03-06
Try removing the content of the directory "~/.local/share/gvfs-metadata", or better rename that dir, just to be sure.

Note that this will reset all your per-folder set view options.

---

