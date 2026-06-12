---
title: "Embed terminal on desktop"
date: 2013-04-08
forum: Desktop Environments
---

### Post by stayhard on 2013-04-08
Hi!

Im trying to embedd the xubuntu terminal on the desktop (xfce4-terminal) but it is not work like I want.
I have changed background, text color, removed menys etc etc.
I installed compiz, but I only get the autostart to work.

When the computer starts the terminal starts but like any other software, it lays in the left upper corner and it is still in the meny,
so I can right click it and maximize, preference, exit etc etc.

Pls help!

Using latest xubuntu and latest compiz

---

### Post by ajgreeny on 2013-04-08
I am not totally sure what you are trying to do, but it sounds as if you want your desktop to contain just fullscreen terminal

You can do the fullscreen start easily by changing the command in the autostart list of the xubuntu settings manager that you probably have at the moment to read ```
xfce4-terminal --fullscreen
``` Try it in the Alt+F2 run box and you'll see what I mean. You can remove the menubar etc etc, by using the addition of --hide-menubar --hide-toolbars --hide-borders.

```
xfce4-terminal --fullscreen --hide-menubar --hide-toolbars --hide-borders
``` will give you nothing but a fullscreen terminal with just the scrollbar showing on the right hand side.

Users will still be able to start other graphical applications with the terminal commands, of course.
If you want that to not be an option (without more knowledge of Linux) you could start the computer in text mode, ie, not go straight to an xfce desktop by editing other files in the system.  Let us know what it is that you really want.

---

