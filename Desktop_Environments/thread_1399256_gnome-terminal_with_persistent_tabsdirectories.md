---
title: "gnome-terminal with persistent tabs/directories?"
date: 2010-02-05
forum: Desktop Environments
---

### Post by MgFrobozz on 2010-02-05
I'm using gdm with the releases shown below. I generally have one gnome-terminal open, with 10 tabs, each with a custom title, and the shell of each tab in a different directory.

When I update and a new kernel installation is required, and then reboot, then I need to re-open gnome-terminal, re-create the tabs and titles, and reset the directories for each, and restart the applications that were running in about half of the tabs. 

Is there a way to make this persistent, so that when I "shutdown -r", the gnome-terminal tabs and titles are saved somewhere, and re-created when I open gnome-terminal? If it also restored the working directory, that would be even better.

Btw, I searched for "gnome-terminal" in various combinations with "tab", "persistent", and "session", but didn't find the answer to this one. Any help greatly appreciated.

```

> dpkg --status gnome-terminal | grep Version
Version: 2.28.1-0ubuntu1
> cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
> uname -r
2.6.31-17-generic

```

---

