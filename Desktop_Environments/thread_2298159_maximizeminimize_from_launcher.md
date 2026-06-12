---
title: "maximize/minimize from launcher"
date: 2015-10-09
forum: Desktop Environments
---

### Post by dkerlee on 2015-10-09
I'd like to suggest a GUI improvement. From the default launcher, on the side, when clicked once, the application comes up, when clicked again, it minimizes. At the moment, the second click doesn't do anything other than re-bring-it-to-the-front.
thanks!

---

### Post by howefield on 2015-10-09
That is now a user configurable option, at least in later releases. Not sure which release it was first to include, may have been 15.04.

---

### Post by deadflowr on 2015-10-09
^^First included in 14.04.
There is a ppa for 12.04.

You need to either install a utility tool such as compizconfig-settings-manager, unity-tweak-tool, or dconf-editor.
(howefield's is unity-tweak-tool --as seen from the screenie)

or run
```
dconf write /org/compiz/profiles/unity/plugins/unityshell/launcher-minimize-window true
```
from a terminal.

Note: it's considered an unsupported action, so anything that you might not like about it will not be fixed.
(And it has various actions that you may find irritating, like how it handles multiple windows for the same app, and how it handles windows on different workspaces, among other things.
Though, taking it as a whole, it works great)

Enjoy

---

### Post by dkerlee on 2015-10-09
thank you!

---

