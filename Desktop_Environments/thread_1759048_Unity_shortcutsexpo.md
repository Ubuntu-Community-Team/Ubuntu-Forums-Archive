---
title: "Unity shortcuts/expo"
date: 2011-05-15
forum: Desktop Environments
---

### Post by AntoineT on 2011-05-15
Hello,

In Unity, <super><w> zooms out on all windows on all workspaces. When multiple instances of an app are open, clicking on the launcher icon zooms out on all windows from that application. Is there a keyboard shortcut (or a way to create such a shortcut) to zoom out on all windows from the currectly focused application. For example, if you have 2 Chromium windows and 3 Evince windows, and the focus is on Evince, <super><w> will zoom out on all 5 windows. I would like to define a shortcut to zoom out on the 3 Evince windows, just as if I clicked on the Evince incon on the launcher.

Antoine

---

### Post by Bonster on 2011-05-15
Make sure you have ccsm installed

> sudo apt-get install compizconfig-settings-manager

Then open it and go to the '**scale plugin**'

What you want is the '**Initiate Windows Picker for Windows Group**'

You can setup using the keyboard icon for hotkey, mouse/monitor for hotcorner. Just depends on how you want to activate it

---

### Post by AntoineT on 2011-05-15
Thanks, It should indeed workn but in fact doesn't, at least on my machine. As a matter of fact I found this bug report [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/774059](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/774059) which describes the problem.

Antoine

---

