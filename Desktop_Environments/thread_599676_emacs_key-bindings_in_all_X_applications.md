---
title: "emacs key-bindings in all X applications"
date: 2007-11-01
forum: Desktop Environments
---

### Post by marra on 2007-11-01
I am looking for a way to enable emacs key-bindings in not only the terminal (which can be done, I know, with the command set -o emacs), but also in all X applications, including Firefox, Thunderbird, Open Office etc.

In Windows there is a nice program called XKeymacs that does this across all applications.  Is there an equivalently simple way to create/define these emacs key bindings in X apps in Ubuntu?

Any help is greatly appreciated!

---

### Post by shev on 2007-12-12
I'm also looking for a way to have emacs keybindings across all apps, like xkeymacs on windows.  Surely now that I've moved to Linux there's a way to do this?!

---

### Post by shev on 2007-12-13
Supposedly this command, from [http://kb.mozillazine.org/Emacs_Keybindings_%28Firefox%29](http://kb.mozillazine.org/Emacs_Keybindings_%28Firefox%29), will do the trick:

 gconftool-2 --set /desktop/gnome/interface/gtk_key_theme Emacs --type string

However on my 7.10 gutsy, amd64 fresh install, it does nothing in either Firefox or the rest of the system.  Firing up gconf-editor shows the setting is there, but still no juice.  Can anyone help please?

---

### Post by shev on 2007-12-13
Well in fact setting the gtk_key_theme does work, but the change is not global; apps can override the emacs keybindings with their own bindings.  For firefox and thunderbird, one has to disable some of the the default bindings (e.g. ctrl-p, ctrl-n); there's an extension, keyconfig, which is required:

[http://mozilla.dorando.at/readme.html](http://mozilla.dorando.at/readme.html)

Look on the page for a link to keyconfig (not exactly clear at first), then install it.  For thunderbird, you need to download it, then install it separately.  Then disable the keybindings where you want emacs keys to work.

There does not seem to be a tool like xkeymacs which proactively catches keyboard commands and applies them to any app, and that's a big disappointment for those of us with emacs hardwired into us. :-(

---

### Post by dast on 2008-01-05
Is anyone else having this problem under Gutsy?

I've set the Emacs setting under gconf, which seems to work in at least *some* applications.  Firefox seems fine, gedit seems fine.  However, nautilus seems to partially ignore this setting, which is a real PITA.  Some keys seem okay (Ctrl-E, Ctrl-K), but others (Ctrl-W, Ctrl-A) are broken.

This all worked fine under Fiesty, IIRC.  However, I did a fresh install of Gutsy and it does not seem to work like before.

One other thing.. Open Office seems to have always ignored this setting.  Anyone know how to get Open Office to use emacs keybindings?

---

