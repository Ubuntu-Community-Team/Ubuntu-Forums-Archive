---
title: "Thunar OpenTerminal alternative command"
date: 2011-11-14
forum: Desktop Environments
---

### Post by paalz on 2011-11-14
Hi all!

In out-of-the-box thunar "Open terminal" command is shown in context menu for directories only. However it is not always comfortable. If you want to "Open terminal" menu item apper for every file in the folder so that you don't bother where to click to open terminal for the cwd, go to "Edit -> custom actions" and change the "Open terminal" command to
```
[ -d "%f" ] && exo-open --working-directory %f --launch TerminalEmulator || exo-open --working-directory $(dirname %f) --launch TerminalEmulator
```then on the next tab check the "other files" checkbox.

now the "Open terminal" will be shown in popup menu for every type of file and will correctly open terminal in current working directory.

---

### Post by ankspo71 on 2011-11-16
Thanks, this works for me.

---

