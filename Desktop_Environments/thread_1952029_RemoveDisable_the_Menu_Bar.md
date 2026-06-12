---
title: "Remove/Disable the Menu Bar"
date: 2012-04-03
forum: Desktop Environments
---

### Post by Renor on 2012-04-03
Hello,

I use Ubuntu 10.04 Lucid Lynx and I try to remove, hide or disable the top menu bar from the Desktop.
I can easily achieve that on the GUI by right clicking on it and then choosing "Delete This Panel" but I would need to be able to do the same thing **in command line** as I am trying to incorporate this on a liveCD (I am using UCK to build the liveCD so I only have access to a console during the build).

I tried to remove files linked to gnome-panel or gnome-menus but it did not change anything.

I also found threads talking about uninstalling packages such as  indicator-appmenu but for other versions of Ubuntu. I haven't been able to find any for 10.04.
Actually I get nothing when I do:
```
apt-cache search appmenu
```

Would anyone have an idea on how to do that?

Thanks!

---

### Post by na5h on 2012-04-03
Perhaps [this thread]("http://ubuntuforums.org/showthread.php?t=1271278") will help...

---

### Post by Renor on 2012-04-03
It seems to be what I need. I can manage to hide it, I'll try to add that to the build process of the liveCD and test it.

Edit: Actually, just removing the gnome-panel file from the /usr/bin/ folder during the build prevented the top and bottom bar from launching. Didn't even need to kill the process.

Thanks a lot!

---

