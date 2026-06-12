---
title: "Missing top panel"
date: 2009-02-12
forum: Desktop Environments
---

### Post by grantcentral on 2009-02-12
Help me!
I had the stick notes application go nuts and place numerous sticky notes on the top panel. I tried to remove them individually but to no avail. It covered over the apps on the top panel so they are no longer accessible. :confused:

Now the top panel has disappeared after a reboot. :( Does anyone have an idea how to get the panel back? Then after that does anyone have an idea how to get rid of all the sticky notes?

Thanks
Bill
:popcorn:

---

### Post by WatchingThePain on 2009-02-12
Hi,

Yeah click on the other panel and choose add panel.
It's just right clicking.
You can customise what's on the panel.
You can remove the notes application from add remove software.

---

### Post by Simian Man on 2009-02-12
Right click on the bottom panel and choose "New Panel".  Then add stuff to it by right-clicking the new panel and choosing "Add to Panel".

---

### Post by UbuntuNerd on 2009-02-12
type this commands in a terminal all at once to restore your panels to default like it was before:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by jflaker on 2009-02-12
> **UbuntuNerd said:**
> type this commands in a terminal all at once to restore your panels to default like it was before:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```


I just had to do that about 4 hours ago because my panels were all messed.....rm the panel folder then logout/login and the panels will be restored to "out of the box".

---

### Post by jjcylk on 2010-07-28
I glad this was out there. I am another newbie & blew away my top panel. This restored it like I wanted:D

---

