---
title: "Keyboard shortcuts don't work properly"
date: 2009-05-16
forum: General Help
---

### Post by fizikz on 2009-05-16
I've noticed that some keyboard shortcuts (set in System -> Preferences -> Keyboard Shortcuts) just don't work. For instance, "Run a terminal" or "Take a screenshot" are mapped to keyboard shortcuts (and the keypress is recognized when setting the shortcut) but pressing the keyboard shortcut buttons does nothing. For the terminal, I set a custom shortcut to launch gnome-terminal, and this works. However, for screenshots, even the custom keyboard shortcut set to execute gnome-panel-screenshot doesn't work. They worked fine in Ubuntu 8.10, but haven't worked since the upgrade to 9.04.

---

### Post by FIONEX on 2009-05-16
It's compiz...

Compiz overrides those shortcuts.  Run this command in a terminal:
```

sudo apt-get install compizconfig-settings-manager

```

Then go to System -> Preferences -> CompizConfig Settings Manager
Look under General Options -> Key Bindings   OR   Commands --> Key Bindings

You can specify your own shortcuts under "Commands", and then attach a Keyboard Shortcut to it under "Commands -> Key Bindings"

---

### Post by fizikz on 2009-05-16
Is the gnome keyboard shortcut menu of no use anymore? And if so, why is it still there?

Maybe I'm doing something wrong, but when I tried setting key bindings in compiz settings manager, for any command I entered, it gave a message "X is not a valid shortcut."

---

### Post by FIONEX on 2009-05-16
I'm really not to sure why but I dont think compiz is active all the time.  And if it's not active, then the default gnome-shortcuts work.

Suppose you want a shortcut to the terminal.  Go into Commands.
For  Command line 0, type  "gnome-terminal"
Then go to the "Key Bindings" tab and click "Disabled" for Command Line 0.  Check the Enabled box.  Then click "Capture key combination" and press the buttons you want together.  I use Ctrl+Windows+Space.  So I press all three buttons at the same time.  Then press OK and you're done!

---

### Post by fizikz on 2009-05-16
Oh, thanks, now I see. I didn't quite get what the Commands tab was for. I was using the Edit button on the Key Bindings tab to try to enter the command. 

I guess you're right that compiz is taking precedence. I run compiz all the time. The confusing bit is that I was able to get some custom commands working via the gnome keyboard shortcut settings.

---

### Post by compabeto on 2009-05-22
@FIONEX, or anyone else who has a solution.

I have a similar problem, but I can remedy it through ccsm as stated above. Is there any way to revert back to using the gnome keyboard shortcuts instead of having to use ccsm because in order to use ccsm you have to know the command names to call. Since I lost power of the gnome keyboard shortcuts, I can't do Alt F1 or Alt F2, and since their commands have been removed and incorporated into gnome-panel according to [http://ubuntuforums.org/showthread.php?t=512290]("http://ubuntuforums.org/showthread.php?t=512290"), I can't shortcut them through ccsm. I know there are workarounds, but I would like to use the default setup if possible, if not no biggie.

---

