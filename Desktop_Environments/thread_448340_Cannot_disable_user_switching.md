---
title: "Cannot disable user switching"
date: 2007-05-19
forum: Desktop Environments
---

### Post by Pausanias on 2007-05-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/114945](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/114945) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Title says it all. I can't disable the "Switch User..." button when my screen is locked. In Configuration Editor, I've checked the "Disable user switching" pref under lockdown, and user_switch_enabled is off under gnome-screensaver. No response from launchpad, so hoping for help here.

Edit: this used to work in Edgy.

---

### Post by alfayate on 2007-08-09
Have you tried doing as root:

chmod o-x /usr/bin/gdmflexiserver


Don't know if this is going to work with the screensaver, but at least it should disable the main user switch button.

Good luck!

---

