---
title: "installed Terminal but it won't run"
date: 2005-10-23
forum: Desktop Environments
---

### Post by jnoreiko on 2005-10-23
I've just installed Terminal with Gnome App Install.
I don't mean the GNOME terminal, but another terminal program that's listed as 'Terminal' in the program list. Its full description is:

> Terminal
Terminal Emulator

This package contains Terminal, which is a lightweight and easy to use terminal emulator for X11. It was created to fit nicely into the Xfce desktop environment, but it also fits nice with other environments.
For people that already know GNOME 2 terminal and are searching for a lighter but comparable replacement, Terminal might be the answer.
Homepage: [http://terminal.os-cillation.com/](http://terminal.os-cillation.com/)

Just so it's clear which one I mean :)

Installation goes fine, but when I select it from the apps menu, I get this:

> 
Cannot launch entry

Details: Failed to execute child process "Terminal" (No such file or directory)

---

### Post by SilentCacophony on 2005-10-23
Hi. That's a nice terminal emulator, but there appears to be a bug in the istall script for that app. The menu entry points to a non-existant file 'Terminal', whereas the actual file is 'xfce4-terminal'. 

Perhaps the easiest way to remedy that would be to issue this from another terminal, then 'Terminal' will be symlinked to 'xfce4-terminal':

**sudo ln -s /usr/bin/xfce4-terminal /usr/bin/Terminal**

After that you may use either name to reference it.

---

### Post by jnoreiko on 2005-10-24
Cool.

My main reason for trying it is the bug in gnome terminal with dragging files whose path has a space in it.
The bug is reported lots of times, but is marked as wontfix.

( [http://bugzilla.gnome.org/show_bug.cgi?id=85926](http://bugzilla.gnome.org/show_bug.cgi?id=85926), [http://bugzilla.gnome.org/show_bug.cgi?id=134272](http://bugzilla.gnome.org/show_bug.cgi?id=134272) )

---

### Post by jnoreiko on 2005-10-24
The fix works :)

However, this terminal suffers from the same problem :(
On the plus side, it lets you remap keyboard shortcuts, so I can get copy and paste to work properly at least :)

---

