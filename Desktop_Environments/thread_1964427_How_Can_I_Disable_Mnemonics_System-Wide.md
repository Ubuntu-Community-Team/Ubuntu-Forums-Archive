---
title: "How Can I Disable Mnemonics System-Wide"
date: 2012-04-24
forum: Desktop Environments
---

### Post by andymandias on 2012-04-24
I recently upgraded from 10.10 to 11.10 and mnemonics (alt-key access to menus) have come back.  I like to use Emacs key bindings in a variety of programs, and they class with many of the default bindings (e.g. ctrl-a for move to beginning of line and select all).  My previous solution was to map many of the non-Emacs key bindings to use alt as the accelerator, but that doesn't work well when mnemonics are enabled.

Back in 10.10 I was able to disable mnemonics system-wide (more or less) by having a ~/.gtkrc with the line:

gtk-enable-mnemonics = 0

in it.  However, that no longer seems to work.  I've tried adding ~/.gtkrc-2.0 and ~/.gtkrc-3.0 files.  I've tried modifying the /etc/gtk-2.0/settings.ini file and /etc/gtk-3.0/settings.ini file to look like:

[Settings]
gtk-enable-mnemonics = 0

From the following page:

[http://developer.gnome.org/gtk3/3.2/GtkSettings.html#GtkSettings--gtk-enable-mnemonics](http://developer.gnome.org/gtk3/3.2/GtkSettings.html#GtkSettings--gtk-enable-mnemonics)

it seems like the option is still available in some form, but I'm at a bit of a loss how to enact it or if it's even possible to do so.

Any help would be greatly appreciated!

---

### Post by RichardCain on 2012-04-24
What DE are you running?

In Gnome shell, open Advanced Settings, click on "Theme" and there is an option to select Emacs bindings.

EDIT: If it's not already installed, you may need to run:
```
sudo apt-get install gnome-tweak-tool
```

---

### Post by andymandias on 2012-04-24
Thanks for the DE question, I think I may have mislabeled this thread.  I was running Unity under 11.10, but now I'm running Gnome-Shell under 11.10.  Gnome-Shell does not have this problem, and I think I can get used to all its differences.  I'm going to go ahead and mark this as solved.

---

