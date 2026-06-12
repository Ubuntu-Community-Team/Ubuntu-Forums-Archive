---
title: "Simple Metacity Question"
date: 2007-06-12
forum: Desktop Environments
---

### Post by Sweet Mercury on 2007-06-12
This is a simple question, really.

I don't have a workspace switcher in my GNOME panel, I don't need it. However, I can't seem to access the workspace switcher configuration without it. Is there a terminal command to get there? If so I can build a launcher no problem.

Otherwise, I have to either keep it on my panel, which I don't want, or I have to put one on the panel, right click to get to the configuration, set it, then delete it fromt he panel.

Or am I missing where the settings are?

---

### Post by tturrisi on 2007-06-12
You can edit the default setting if have the Configuration Editor installed:
~$#  gconf-editor
drill to Apps > Panel > Default Setup > Applets > Workspace Switcher

---

### Post by Sweet Mercury on 2007-06-12
> **tturrisi said:**
> You can edit the default setting if have the Configuration Editor installed:
~$#  gconf-editor
drill to Apps > Panel > Default Setup > Applets > Workspace Switcher


Yeah, I found that, but it doesn't let me change the number of workspaces or the number of rows, etc. That's what I wanted to be able to access on the fly without having the switcher in my panel.

Thanks though. I'm experimenting with replacing Metacity with Enlightenment, so maybe this will be a moot point anyway. (A thread on those problems forthcoming.)

---

