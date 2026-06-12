---
title: "compiz/beryl noob problem"
date: 2007-10-23
forum: Desktop Environments
---

### Post by pinkmonkey on 2007-10-23
I've only been using Ubuntu (and Linux)for two days and it's been fairly painless... Everything has been working great and the problems I've been having have been minor at worst. Because I'm a total noob I also didn't know that compiz came pre-installed in GutsyGibbon and installed it anyway, and what I think is an older version of beryl. It was working... kinda but when I restarted my computer it stopped working completely. I think it keeps crashing and returning to the default window controller.This isn't a huge problem sine the computer is still works fine. But this computer is my sisters and I want her fist Linux experinace to be as great as possible, Can anyone please help me undo what I did.

---

### Post by ohzopants on 2007-10-30
First you should go to Synaptic, search for beryl and remove all the relevant packages.

Then you should probably run
```
sudo apt-get autoremove
```
in the terminal.  This will remove any packages that were installed to meet dependencies of other packages that have since been removed.

Then go to the Appearance Preferences dialog (System -> Preferences -> Appearance) and choose no effects on the Visual Effects tab.

At this point, do a reboot, just to be sure.

When your system starts up again, re-enable desktop effects from the Appearance Preferences dialog.

---

