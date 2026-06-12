---
title: "Gnome-panel hangs when I try to quit"
date: 2007-01-18
forum: Desktop Environments
---

### Post by haxality on 2007-01-18
Hello, I'm having a semi-frustrating problem with gnome. When I click the 'quit' button that normally brings up the dialog of options (shutdown, restart, logout, suspend, hibernate, etc), gnome-panel freezes. I can only get it back by using 'killall gnome-panel' and waiting for it to restart. Also, the main reason this is a problem is because I can only get out of gnome by using ctrl-alt-backspace. I am using a Toshiba Tecra M1 Laptop with Dapper Drake installed. Help would be greatly appreciated.


EDIT: Figured out what the problem was. Enabling suspend support breaks gnome-panel for some reason.

---

### Post by haxality on 2007-01-19
This problem is incredibly frustrating. I did a complete reinstall and it still happened again. It's completely random. Some sort of help would be awesome.

---

### Post by gametime on 2007-02-26
I'm also having the same problem.  Has anyone found what causes this?

---

### Post by jeffus_il on 2007-12-21
Me too, Seems to be a problem with the .gnome2 directory contents as another user on the same machine has no problem. don't reinstall just do Ctrl-Alt-Backspace until it comes right ....

---

### Post by jeffus_il on 2007-12-21
Ok, disabled the hibernate and suspend buttons in gconf-editor under the power manager and worked around the problem

---

### Post by jeffus_il on 2007-12-21
More.. Reboted and still had the problem, found that the pwer manager daemon was not running, ran it in a terminal window (gnome-power-manager& ) and fixed - for the moment

---

