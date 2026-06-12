---
title: "fluxbox help needed"
date: 2008-08-08
forum: Desktop Environments
---

### Post by whitey on 2008-08-08
Hey Guys,

So i've used fluxbox for years, and for the most part I've never really had any trouble until today.  I move my monitor cable, and it unseated my pci video card.  I had to reboot my box, and after it came back up, I could still log into fluxbox without issue, but nothing in the fluxbox menu works.  :(

I switched over to gnome for know, but would like to go back to fluxbox, anybody else see this happen?  I haven't been able to find anything in the xorg logs, and I don't think fluxbox logs its own actions.

---

### Post by whitey on 2008-08-08
I've turned on logging in ~/.fluxbox/startup, and here are the logs that I'm getting:

```
whitey@yamato:~$ cat /home/whitey/.fluxbox/log 
------------------------------------------
Log File: /home/whitey/.fluxbox/log
Fluxbox version: 1.0.0
Compiled: Dec  9 2007 21:45:56
Compiler: GCC
Compiler version: 4.2.3 20071123 (prerelease) (Ubuntu 4.2.2-3ubuntu4)

Defaults:
    menu: /etc/X11/fluxbox/fluxbox.menu-user
   style: /usr/share/fluxbox/styles/BlueNight
    keys: /etc/X11/fluxbox/keys
    init: /etc/X11/fluxbox/init
     nls: /usr/share/fluxbox/nls

Compiled options (- => disabled): 
-DEBUG
EWMH
GNOME
IMLIB2
KDE
NLS
REMEMBER
RENDER
SHAPE
SLIT
TOOLBAR
XFT
XINERAMA
XMB
XPM

------------------------------------------
Failed to read: session.styleFile
Setting default value
Failed to read: session.styleFile
Setting default value
Failed to read: session.styleFile
Setting default value
Failed to read theme item: window.roundCorners
Failed to read theme item: window.title.height
Failed to read theme item: window.close.pixmap
Failed to read theme item: window.close.unfocus.pixmap
Failed to read theme item: window.close.pressed.pixmap
Failed to read theme item: window.maximize.pixmap
Failed to read theme item: window.maximize.unfocus.pixmap
Failed to read theme item: window.maximize.pressed.pixmap
Failed to read theme item: window.iconify.pixmap
Failed to read theme item: window.iconify.unfocus.pixmap
Failed to read theme item: window.iconify.pressed.pixmap
Failed to read theme item: window.shade.pixmap
Failed to read theme item: window.shade.unfocus.pixmap
Failed to read theme item: window.shade.pressed.pixmap
Failed to read theme item: window.unshade.pixmap
Failed to read theme item: window.unshade.unfocus.pixmap
Failed to read theme item: window.unshade.pressed.pixmap
Failed to read theme item: window.menuicon.pixmap
Failed to read theme item: window.menuicon.unfocus.pixmap
Failed to read theme item: window.menuicon.pressed.pixmap
Failed to read theme item: window.title.focus.pixmap
Failed to read theme item: window.title.unfocus.pixmap
Failed to read theme item: window.stick.pixmap
Failed to read theme item: window.stick.unfocus.pixmap
Failed to read theme item: window.stick.pressed.pixmap
Failed to read theme item: window.stuck.pixmap
Failed to read theme item: window.stuck.unfocus.pixmap
Failed to read theme item: menu.frame.underlineColor
Theme: Error loading font (utf8)for "menu.title.font" or "Menu.Title.Font": -*-dejavu-bold-r-*-*-11-*-*-*-*-*-*-*
Theme: Setting default value
Failed to read theme item: menu.titleHeight
Failed to read theme item: menu.itemHeight
Failed to read theme item: menu.submenu.pixmap
Failed to read theme item: menu.selected.pixmap
Failed to read theme item: menu.unselected.pixmap
Failed to read theme item: menu.hilite.submenu.pixmap
Failed to read theme item: menu.hilite.selected.pixmap
Failed to read theme item: menu.hilite.unselected.pixmap
Failed to read theme item: menu.roundCorners
Failed to read theme item: toolbar.iconbar.borderWidth
Failed to read theme item: toolbar.iconbar.borderColor
Failed to read theme item: toolbar.iconbar.focused.justify
Failed to read theme item: toolbar.iconbar.unfocused.justify
Failed to read theme item: window.roundCorners
Failed to read theme item: window.title.height
Failed to read theme item: window.close.pixmap
Failed to read theme item: window.close.unfocus.pixmap
Failed to read theme item: window.close.pressed.pixmap
Failed to read theme item: window.maximize.pixmap
Failed to read theme item: window.maximize.unfocus.pixmap
Failed to read theme item: window.maximize.pressed.pixmap
Failed to read theme item: window.iconify.pixmap
Failed to read theme item: window.iconify.unfocus.pixmap
Failed to read theme item: window.iconify.pressed.pixmap
Failed to read theme item: window.shade.pixmap
Failed to read theme item: window.shade.unfocus.pixmap
Failed to read theme item: window.shade.pressed.pixmap
Failed to read theme item: window.unshade.pixmap
Failed to read theme item: window.unshade.unfocus.pixmap
Failed to read theme item: window.unshade.pressed.pixmap
Failed to read theme item: window.menuicon.pixmap
Failed to read theme item: window.menuicon.unfocus.pixmap
Failed to read theme item: window.menuicon.pressed.pixmap
Failed to read theme item: window.title.focus.pixmap
Failed to read theme item: window.title.unfocus.pixmap
Failed to read theme item: window.stick.pixmap
Failed to read theme item: window.stick.unfocus.pixmap
Failed to read theme item: window.stick.pressed.pixmap
Failed to read theme item: window.stuck.pixmap
Failed to read theme item: window.stuck.unfocus.pixmap
Failed to read theme item: menu.frame.underlineColor
Theme: Error loading font (utf8)for "menu.title.font" or "Menu.Title.Font": -*-dejavu-bold-r-*-*-11-*-*-*-*-*-*-*
Theme: Setting default value
Failed to read theme item: menu.titleHeight
Failed to read theme item: menu.itemHeight
Failed to read theme item: menu.submenu.pixmap
Failed to read theme item: menu.selected.pixmap
Failed to read theme item: menu.unselected.pixmap
Failed to read theme item: menu.hilite.submenu.pixmap
Failed to read theme item: menu.hilite.selected.pixmap
Failed to read theme item: menu.hilite.unselected.pixmap
Failed to read theme item: menu.roundCorners
Failed to read theme item: slit.bevelWidth
Failed to read theme item: toolbar.shaped
Failed to read theme item: toolbar.height
Failed to read theme item: toolbar.button.size
Failed to read theme item: toolbar.clock.font
Failed to read theme item: toolbar.clock.borderWidth
Failed to read theme item: toolbar.clock.borderColor
Failed to read theme item: toolbar.button.font
Failed to read theme item: toolbar.button.textColor
Failed to read theme item: toolbar.button.borderWidth
Failed to read theme item: toolbar.button.borderColor
Failed to read theme item: toolbar.button.scale
Failed to read theme item: toolbar.workspace.font
Failed to read theme item: toolbar.workspace.borderWidth
Failed to read theme item: toolbar.workspace.borderColor
Failed to read theme item: toolbar.systray.font
Failed to read theme item: toolbar.systray.textColor
Failed to read theme item: toolbar.systray.borderWidth
Failed to read theme item: toolbar.systray.borderColor
Failed to read theme item: toolbar.systray.scale
Failed to read theme item: toolbar.iconbar.borderWidth
Failed to read theme item: toolbar.iconbar.borderColor
Failed to read theme item: toolbar.iconbar.focused.justify
Failed to read theme item: toolbar.iconbar.unfocused.justify
whitey@yamato:~$ 


```

---

### Post by Sycron on 2008-08-08
I don't understand your problem, can you be please more specific ?

---

### Post by whitey on 2008-08-08
Hello,

I ended up solving my own issue, there was something .fluxbox directory that was corrupt.  I must have fat fingered something important when I was editing my config files, well long story short, I ended up deleting the ~/.fluxbox directory and had it remade.  All is good

---

### Post by annda on 2008-08-08
after a long break i tried coming back to fluxbox just today and had the same problem. most customizations worked but - in my case - configuring key shortcuts for switching workspaces broke the menu repeatedly (although the shortcuts kept working). even reversing the changes didn't help, .fluxbox/ hat to be wiped clean.

do you know what your problem may have been?

---

### Post by RedSquirrel on 2008-08-08
> **annda said:**
> after a long break i tried coming back to fluxbox just today and had the same problem. most customizations worked but - in my case - configuring key shortcuts for switching workspaces broke the menu repeatedly (although the shortcuts kept working). even reversing the changes didn't help, .fluxbox/ hat to be wiped clean.

do you know what your problem may have been?
By any chance, were you using fluxkeys? That's been known to cause problems.

---

### Post by annda on 2008-08-08
> **RedSquirrel said:**
> By any chance, were you using fluxkeys? That's been known to cause problems.

at first i was, but then i went kosher and modified the keys file directly, with the same result. do we have a problem with the latest fluxbox package?

---

### Post by RedSquirrel on 2008-08-08
> **annda said:**
> at first i was, but then i went kosher and modified the keys file directly, with the same result. do we have a problem with the latest fluxbox package?
I'm not certain. The package seemed OK to me, but I only used the one on Hardy very briefly.

I do recall that fluxkeys puts incorrect lines in the keys file. If those lines were still in the keys file you modified directly, you would still have problems. It goes without saying that the keys file must be *error-free* or strange things can happen. :)

The fluxconf package is not maintained anymore and as far as I know the Fluxbox developers discourage its use.

**Edit:** ... and post your ~/.fluxbox/keys file if you're still having trouble with it. ;)

---

