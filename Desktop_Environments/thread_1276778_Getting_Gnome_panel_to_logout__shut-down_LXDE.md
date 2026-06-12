---
title: "Getting Gnome panel to logout / shut-down LXDE"
date: 2009-09-27
forum: Desktop Environments
---

### Post by Lukios on 2009-09-27
I have been able to install and use gnome-panel successfully, but I have not been able to get it to shutdown or logout of LXDE. I have resorted to making my own shutdown Icon for the panel, but I was hoping someone could show me how to edit the menu to point to the lxde-logout. Any help is appreciated. Also if someone knows how to do the same thing for the Mint custom menu I would appreciate that too.

Thanks in advance.

---

### Post by Lukios on 2009-10-06
anyone

---

### Post by ankspo71 on 2009-10-07
Hi
Here is the command for the LXDE shutdown and logout screen.
```
lxsession-logout

```
James

---

### Post by earthpigg on 2009-10-07
> **ankspo71 said:**
> Hi
Here is the command for the LXDE shutdown and logout screen.
```
lxsession-logout

```
James

beat me to it.

hunt around in your ~/.gconf and other gnome-panel related dotfiles.

---

### Post by Lukios on 2009-10-07
Already knew the lxde-logout, that was obvious, and I looked in my config files and gconf, cant find anything. Thanks for the pots though. Let me know if you find out anything.

---

### Post by Lukios on 2009-10-07
I figured out how to get mintMenu (which is based off of gmenu) to logout of lxsession instead of gnome-session. I have placed the tutorial here.

[http://ubuntuforums.org/showthread.php?p=7971101#post7971101](http://ubuntuforums.org/showthread.php?p=7971101#post7971101)

I am still trying to figure out how to get the gnome-menu (both the custom bar menu and the original) to logout of the lxsession. Any help is appreciated.

---

