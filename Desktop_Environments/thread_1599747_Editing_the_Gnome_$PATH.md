---
title: "Editing the Gnome $PATH"
date: 2010-10-18
forum: Desktop Environments
---

### Post by AbtZ on 2010-10-18
I'd like to add a keyboard shortcut in Gnome that runs [dmenu]("http://tools.suckless.org/dmenu/"), which is located in ~/bin/ (I'm on a school computer, no sudo access to /usr/bin).

If I run dmenu from the Run dialog (Alt+F2, typing "bin/dmenu_run") it works. After trying to set up a new keyboard shortcut, in System->Preferences->Keyboard Shortcuts, it doesn't run dmenu.

I think it has to do with Gnome not looking in ~/bin for executable files. How do I update Gnome's $PATH variable? 

Updating $PATH through for example .profile or .zshrc only works if I want to run dmenu from the terminal -- which I don't.

---

