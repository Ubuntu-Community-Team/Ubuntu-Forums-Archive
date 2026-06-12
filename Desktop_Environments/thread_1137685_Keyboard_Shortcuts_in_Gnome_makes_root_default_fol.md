---
title: "Keyboard Shortcuts in Gnome makes root default folder"
date: 2009-04-25
forum: Desktop Environments
---

### Post by kesshaka on 2009-04-25
Hi all! This is my first time posting on these forums, as up until now I have always been able to find solutions to my problems by googling. Not so this time..

The issue is that when I create custom shortcuts to launch applications, via System > Preferences > Keyboard Shortcuts, the launched programs default folder change (usually from ~) into / (as in the root filesystem directory). I assume it's the same with every program, although the only ones where I've noticed this is gnome-terminal and emacs, simply because I have not worked with folders in any other apps.

Any help would be greatly appreciated!

Thanks,
Ivar

---

### Post by kesshaka on 2009-05-05
bump

---

### Post by ojrac on 2009-08-11
This was driving me nuts, too. Just change your keyboard shortcut to specify the terminal's working directory:

gnome-terminal --working-directory=~/

---

