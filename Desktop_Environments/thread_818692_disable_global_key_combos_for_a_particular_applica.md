---
title: "disable global key combos for a particular application?"
date: 2008-06-04
forum: Desktop Environments
---

### Post by tupfzom on 2008-06-04
I'm running a DOS program in dosemu that uses the key combinations Alt+F1 to Alt+F10 for some commands, but at least some of those combinations are assigned to something different by the desktop environment (most importantly Alt+F4 for closing a window). Dos**box** catches those key combinations if the mouse is "trapped" inside, but Dosbox is not an option for this particular program because it screws up other things and crashes this DOS program more frequently. Dos**emu** runs the program quite nicely, except for those key combos.

Is there a way of disabling keyboard shortcuts for specific programs?

My idea would be to automatically run a script that disables/enables the (global) shortcuts whenever Dosemu gets/loses the focus. I frequently switch between the DOS program and other programs, so it's important that the scripts are triggered automatically.

For Gnome, those shortcuts can be set using gconftool-2. The Gnome-keys for the shortcuts can be found under */apps/metacity/window_keybindings* and */apps/metacity/global_keybindings*, so I believe that the window mangager (metacity in this case) is responsible for catching/managing the shortcuts. If this is right I need a window manager that
[LIST=a]
[*]can trigger scripts upon a window getting/losing the focus and
[*]is configurable via the command line.
[/LIST]
(I guess the second point should be true for all window managers, but gconftool-2 makes it very simple because no file has to be edited and the changes instantly take effect without restarting metacity/reloading some configuration file or the like.)

So my questions are:
[LIST=a]
[*]Are there any windows managers that support the script triggering?
[*]Are there gconftool-2-equivalents for other window managers?
[/LIST]
Of course it would be simpler if I could configure the shortcuts for each app separately. Does any window manager support that?

TIA

---

### Post by tupfzom on 2008-06-11
I found that Dosemu can grab all keyboard events if pressing Ctrl+Alt+k.  This is great, but it also means that e.g. Alt+Tab (or whatever shortcut is used for switching windows) won't be passed on to the window manger.  So every time I want to switch windows, I have to press Ctrl+Alt+k Alt+Tab, and if I return to the DOS program I have to press Ctrl+Alt+k again (otherwise I might accidentally close the program with Alt+F4).  Any ideas?

---

