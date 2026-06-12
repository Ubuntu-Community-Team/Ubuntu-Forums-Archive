---
title: "Wireless Manager gone"
date: 2007-04-21
forum: Desktop Environments
---

### Post by flipflow on 2007-04-21
Here we go, again ...

Linux newbie deleted the new feisty wireless manager from the panel next to the off-switch (in a bout of frustration about ATI graphics and other stuff). I would like to have it back but is not in list to add to pane. Where can I find it???

Thanx

---

### Post by CameO73 on 2007-04-21
It should normally start automatically, unless you specifically (or unintentionally :)) disabled it.

First of all, check in System --> Preferences --> Sessions if you see a 'Network Manager' in the Startup Programs list. Make sure the checkbox in front of it is enabled. If you don't see a Network Manager item, you can simply create it by doing the following:
[list]
[*]Click on the New button (next to the Startup Programs)
[*]Enter the Name ('Network Manager' comes to mind)
[*]Enter the Command: **nm-applet --sm-disable**
[*]Click Ok and make sure it's enabled (checkbox)
[/list]
After logging out and in again, it should be right back in its rightful place :guitar:

---

