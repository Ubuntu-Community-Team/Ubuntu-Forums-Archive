---
title: "LibreOffice hides taskbar ?"
date: 2012-09-09
forum: Desktop Environments
---

### Post by oygle on 2012-09-09
I have a few apps going , Kubuntu desktop. Task bar is visible. Then I go into LibreOffice spreadsheet, and **NO** task bar, not visible at all.

The only way to navigate is to use a "Windows" trick of ALT-tab.

There is only a 'Close window' icon up the top right hand corner, no minimise and no maximise buttons.

Then I notice it is the same with the other LibreOffice apps (tried writer, same problem).

---

### Post by bra|10n on 2012-09-09
How did you install Kubuntu?

---

### Post by oygle on 2012-09-09
Installed Ubuntu 12.04, then installed Kubuntu-desktop

Can see a bug [here]("https://bugs.launchpad.net/bugs/888743")

---

### Post by bra|10n on 2012-09-09
If LibreOffice was installed prior to you installing kubuntu-desktop then I'm guessing you're missing some necessary support file(s). I can only suggest you run **sudo apt-get update && sudo apt-get dist-upgrade **from within kubuntu to see if that helps.

Ubuntu users may be in a position to help you more with this...
Good luck.

EDIT,
I just noticed your edit. If the bug **IS** in the lo-menubar package then removing lo-menubar should solve your problem.

---

### Post by oygle on 2012-09-09
Okay, thanks for the tip.

I was trying to report the bug, and pressed Ctrl-F2, and all of a sudden LibreOffice now is seen on the task bar, and it has the 3 buttons on the top right hand side (minimise, maximise, close).

Possibly I pressed some other keys that reset window defaults ??

Strange !!

Oygle

---

