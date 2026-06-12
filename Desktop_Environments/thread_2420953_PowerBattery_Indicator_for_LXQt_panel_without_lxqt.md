---
title: "Power/Battery Indicator for LXQt panel without lxqt-powermanagement?"
date: 2019-06-13
forum: Desktop Environments
---

### Post by &amp;wP*!) on 2019-06-13
Is there a way to add a power/battery indicator into the LXQt panel without using lxqt-powermanagement?

After some search on web, I assumed TLP is the best power management tool for Linux. However it is not in default Lubuntu repo. In order to remedy a possible conflict with LXQt tools, I have uninstalled lxqt-powermanagement. But this also removed the power/battery indicator from LXQt Panel. It seems lxqt-powermanagement tool is the only application which adds a power/battery icon into the LXQt panel ( [https://github.com/lxqt/lxqt/issues/1139](https://github.com/lxqt/lxqt/issues/1139) ).

I couldn't find a way to add custom widget into the LXQt panel, also not a separate power/battery indicator Widget. All the available widgets are hardcoded in /usr/share/lxqt/lxqt-panel. All the config files in $HOME/.config/lxqt/ refer to this directory.

Thus I think it is not possible to find a way to link TLP to a power indicator in LXQt panel.

Any thoughts?

---

### Post by &amp;wP*!) on 2019-06-14
I have created an [issue at LXQt Github]("https://github.com/lxqt/lxqt/issues/1722"). The developers responded that they are not aware of any tool other than lxqt-powermanagement tool which can add an icon into the LXQt panel, nor they will implement a generic widget/plugin for any power management tool.

Thus TLP status cannot be shown in LXQt panel, because  as of now nobody is aware of such a LXQt plugin.

I will keep this thread open until someone confirms that there is indeed no tool or way other than lxqt-powermanagement.

---

### Post by CatKiller on 2019-06-14
If you only want to read the battery status, rather than actually fiddling with stuff, you could just use conky for that.

---

### Post by &amp;wP*!) on 2019-06-15
> **CatKiller said:**
> If you only want to read the battery status, rather than actually fiddling with stuff, you could just use conky for that.

Thanks for this. Indeed conky does exactly what I want. I have another issue with conky, but now I will set this to SOLVED.

---

