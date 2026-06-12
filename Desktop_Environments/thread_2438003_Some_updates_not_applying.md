---
title: "Some updates not applying"
date: 2020-03-04
forum: Desktop Environments
---

### Post by freesitebuilder on 2020-03-04
I'm running Ubuntu 18.04 LTS with Gnome, recently upgraded from 16.04 Unity. I have five updates that appear on my top bar, but if I choose "apply now" I just get the Ubuntu Software app which tells me there are no updates outstanding, and the software update loaded from Activities checks for updates and tell me the machine is up-to-date.

The updates are four xserver and one xwayland, all listed in "updates pending". Can I ignore these?
TIA

---

### Post by CelticWarrior on 2020-03-04
You probably can ignore those for the moment.
Or you may install everything with ```
sudo apt update && sudo apt full-upgrade
```

---

