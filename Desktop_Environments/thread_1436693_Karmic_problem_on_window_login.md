---
title: "Karmic problem on window login"
date: 2010-03-23
forum: Desktop Environments
---

### Post by rodhash on 2010-03-23
Hello,

The default login window was really great (Karmic 9.10) untill it changed to a poor and weird color :-(

In a curiosity moment I clicked on a "accessibility button" (in the login window) just to check what were the available options, then the login window changed :?

And I have no option like - "System - Preferences - Login window".

So my question:

How can I back the default login window theme?

I really appreciate any help.

Thanks.

---

### Post by rodhash on 2010-03-23
Hello,

If someone had passed through this issue, follow the steps to fix:

```

sudo -u gdm gconftool-2 -t string -s /apps/metacity/general/theme HumanLogin
sudo -u gdm gconftool-2 -t string -s /desktop/gnome/interface/gtk_theme HumanLogin
sudo -u gdm gconftool-2 -t string -s /desktop/gnome/interface/icon_theme HumanLogin

```

Thanks. :popcorn:

---

