---
title: "Messed up Compiz screen edge setting"
date: 2009-05-14
forum: General Help
---

### Post by Shawn425 on 2009-05-14
Hello, I've managed to mess up my screen edge setting, somehow causing the entire GUI to stop working, whenever I click a button random black areas appear, and I must restart to resolve this, but it continues if I click anything again.
How would I go about completely reinstalling Compiz, or otherwise removing all settings, or changing the screen edge setting back to normal?
I've been struggling with this for 5 hours now, and I'd really like a solution, thanks!

---

### Post by kpkeerthi on 2009-05-14
Install compizconfig-settings-manager. Open it from System -> Preferences. Go to General Settings and there you should find an option to restore all to defaults.

---

### Post by fela on 2009-05-14
When at the desktop, try pressing Alt+F2 and typing ```
metacity --replace
``` And pressing enter. That should stop compiz and replace it with metacity (the default window manager). From there you can easily restore the default compiz settings from ccsm, and run compiz again.

---

