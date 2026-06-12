---
title: "How can I set a compose key in 17.04?"
date: 2017-04-15
forum: Desktop Environments
---

### Post by gwendydd on 2017-04-15
It seems that with Ubuntu Gnome 17.04 the option has vanished from the keyboard settings... or has it moved somewhere else?

---

### Post by x4121 on 2017-04-18
Seems to be a change in latest Gnome-Shell ([https://bugs.launchpad.net/ubuntu/+source/gnome-user-docs/+bug/1683898](https://bugs.launchpad.net/ubuntu/+source/gnome-user-docs/+bug/1683898))

First answer provides a workaround until this is resolved.

> [COLOR=#333333][FONT=monospace]To make <RightCtrl> the compose key, run:
[/FONT][/COLOR][COLOR=#333333][FONT=monospace]gsettings set org.gnome.desktop.input-sources xkb-options "['compose:rctrl']"[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]To see which other keys are possible to use, enter the terminal command:[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]man xkeyboard-config[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]and scroll down to the section "Position of Compose key".[/FONT][/COLOR]

---

### Post by gwendydd on 2017-04-20
Thank you!

I also found I could select a compose key in Gnome Tweak Tool.

---

