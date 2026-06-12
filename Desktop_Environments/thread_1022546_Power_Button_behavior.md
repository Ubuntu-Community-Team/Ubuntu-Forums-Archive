---
title: "Power Button behavior"
date: 2008-12-26
forum: Desktop Environments
---

### Post by sirtrent on 2008-12-26
I've looked around but can't seem to find anything that's quite what I'm looking for.

By default pressing the power button on my laptop brings up a menu allowing me to choose between shutdown, logout, suspend, etc. In the power management preferences this can be altered so that my computer shuts down immediately after pressing the power button.

Problem is the shutdown behavior is different between the two methods. For example, when shutdown is selected from the menu, openoffice will ask to save any unsaved docs(and abort the shut down if the cancel button is pressed) and the shutdown has more splash screen. Whereas if ubuntu is set to shut down immediately when the power button is pressed, gnome quits with no questions asked and lines of text are visible during shutdown.

I want to know if I could get the nicer shutdown behavior to happen when I press my power button.

---

### Post by wootah on 2008-12-26
> **sirtrent said:**
> I've looked around but can't seem to find anything that's quite what I'm looking for.

By default pressing the power button on my laptop brings up a menu allowing me to choose between shutdown, logout, suspend, etc. In the power management preferences this can be altered so that my computer shuts down immediately after pressing the power button.

Problem is the shutdown behavior is different between the two methods. For example, when shutdown is selected from the menu, openoffice will ask to save any unsaved docs(and abort the shut down if the cancel button is pressed) and the shutdown has more splash screen. Whereas if ubuntu is set to shut down immediately when the power button is pressed, gnome quits with no questions asked and lines of text are visible during shutdown.

I want to know if I could get the nicer shutdown behavior to happen when I press my power button.
This is something I never noticed. I was able to reproduce as well, and it seems like it is bug worthy. Perhaps a bug report should be filed.

It seems like it would be something that would be relatively easy to adjust.

---

