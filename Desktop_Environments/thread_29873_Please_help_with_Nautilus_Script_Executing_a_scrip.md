---
title: "Please help with Nautilus Script: Executing a script as root?"
date: 2005-04-26
forum: Desktop Environments
---

### Post by charel on 2005-04-26
Hello,

because I should not ask any questions in the tips and trciks section, i ask here, and I hope someone can help me.
Here [http://www.ubuntuforums.org/showthread.php?t=24008](http://www.ubuntuforums.org/showthread.php?t=24008) and also in the starter guide, someone explaines how to write a nautilus script for open any file as a root.

[I]
"Put the following into ~/.gnome2/nautilus-scripts/Open\ as\ root
Code:
#!/bin/sh gksudo "gnome-open $NAUTILUS_SCRIPT_SELECTED_URIS"
Then make it executable with
Code:
chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root"[/I]



What I need is a script not for opening the file as a root, but for executing a script as a root. Does someone know how to do it?

Thank you.

---

### Post by tread on 2005-04-26
Chown the script to root, and then setuid so the script runs as root every time it runs.

I think this should work:
sudo chown root:root script-name
sudo chmod u+s script-name

That said: Major warning! Letting nautilus run scripts run as root is not the best idea.

---

