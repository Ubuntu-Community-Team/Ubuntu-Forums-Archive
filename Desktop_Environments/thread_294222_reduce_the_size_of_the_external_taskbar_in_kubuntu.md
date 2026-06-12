---
title: "reduce the size of the external taskbar in kubuntu"
date: 2006-11-06
forum: Desktop Environments
---

### Post by rkakkar on 2006-11-06
if you see the screenshot, my external taskbar (added by selecting 'add new panel -> external taskbar') above my kde menu has two rows. i want to reduce it to have only one row. how can i do so?

---

### Post by dbd on 2006-11-06
Right-click the task bar, select configure task bars (or somthing like that, I'm not 100% sure of the name) and then from there you will be able to select the size.

---

### Post by rkakkar on 2006-11-06
nope.. i did that.. but when i select taskbar.. there is no option to set the size.. only option is to set the size of the kde menu bar...

---

### Post by rkakkar on 2006-11-07
anyone else?

---

### Post by maagimies on 2006-11-07
I remember having this problem as well, but I found no information on it. I seemed to be missing a widget in the panel configuration. (The one where you select the panel to be configured, in Kubuntu there's no widget and you config the main one)
Could be a problem with Kubuntus kde/kde default settings.

---

### Post by dbd on 2006-11-07
Sounds like a bug to me.

I've just been looking around the kde settings files and I think I've foundwhere you can configure the size manually. If you goto ~/.kde/share/config/ there will be a file whose name begins with "childpanel_panelextension". If you edit that file and change the line that currently reads "Size=3" (it's probably currently 3, but that is a guess) to read something else like "Size=2" or "Size=1", then log out and log in again then hopefully the size will have changed. If that doesn't work then try doing it when not logged into kde.

---

### Post by ^rooker on 2007-05-01
This seems to be <a href="https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/68926">an already known bug</a>.

There currently exists workaround:
- After adding a new panel, "touch ~/.kde/share/config/kickerrc"

---

### Post by ^rooker on 2007-05-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/68926](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/68926) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This seems to be <a href="https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/68926">an already known bug</a>.

There currently exists workaround:
- After adding a new panel, "touch ~/.kde/share/config/kickerrc"

---

