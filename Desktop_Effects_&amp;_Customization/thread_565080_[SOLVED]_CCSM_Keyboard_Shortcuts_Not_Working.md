---
title: "[SOLVED] CCSM Keyboard Shortcuts Not Working"
date: 2007-10-01
forum: Desktop Effects &amp; Customization
---

### Post by 1212jtraceur on 2007-10-01
So I'm running Compiz Fusion, and have installed xscreensaver. They both work great, except that I can't get <Control><Alt>l (lowercase l) to run "/usr/bin/xscreensaver-command -lock" (the command to lock the screen).

I'm using CCSM to configure the keybindings, and not System > Preferences > Keyboard Shortcuts, so that shouldn't be the problem. In fact, I disabled the Lock Screen binding in the latter, just to make sure there is no conflict.

In CCSM > General Options > Commands, Commands > Command line 0 has the value "/usr/bin/xscreensaver-command -lock", and Key bindings > Run command 0 has the value "<Control><Alt>l" (lowercase l). Why isn't this working?

Thanks,
1212jtraceur

---

### Post by 1212jtraceur on 2007-10-02
SOLVED : googled some more, found [this]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/71030"). Even though its not the same problem, I, on a whim, went into Configuration Editor and changed /apps/gnome-screensaver/mode to "blank-only" and it worked! For anyone with the same problem, keep in mind that the custom binding should be set also.

1212jtraceur

---

