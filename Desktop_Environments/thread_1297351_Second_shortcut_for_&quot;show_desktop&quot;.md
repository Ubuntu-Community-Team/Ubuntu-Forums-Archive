---
title: "Second shortcut for &quot;show desktop&quot;"
date: 2009-10-21
forum: Desktop Environments
---

### Post by eneth80 on 2009-10-21
Hi, 
I want Ctrl+Alt+d to show the desktop, my girlfriend wants Meta+d .
How to add <mod4>d without having to substitute Ctrl+Alt+d?
Basically in gconf-editor >apps>metacity>keybinding_commands, I need a command to do the "show desktop", or I need to duplicate the existing show_desktop in gconf-editor >apps>metacity>global_keybindings

Thanks,
Alex

---

### Post by undecim on 2009-10-21
[http://ubuntuforums.org/showthread.php?t=555829](http://ubuntuforums.org/showthread.php?t=555829)

you should be able to install wmctrl and create a new shortcut in System -> Preferences -> Keyboard Shortcuts

EDIT: only problem is that its an on or off command, rather than a toggle. If you want a toggle, then put this a script in your home directory, run chmod a+x on it, and use that script as the command:
```
#!/bin/bash
if test -e /etc/shm/showdesk; then
  rm /etc/shm/showdesk
  wmctrl -k off
else
  touch /etc/shm/showdesk
  wmctrl -k on
fi
```

---

### Post by stinkeye on 2009-10-22
Give her a separate user account.

---

### Post by 80aless on 2009-10-22
> **undecim said:**
> [http://ubuntuforums.org/showthread.php?t=555829](http://ubuntuforums.org/showthread.php?t=555829)

you should be able to install wmctrl and create a new shortcut in System -> Preferences -> Keyboard Shortcuts

EDIT: only problem is that its an on or off command, rather than a toggle. If you want a toggle, then put this a script in your home directory, run chmod a+x on it, and use that script as the command:
```
#!/bin/bash
if test -e /etc/shm/showdesk; then
  rm /etc/shm/showdesk
  wmctrl -k off
else
  touch /etc/shm/showdesk
  wmctrl -k on
fi
```

Thank you very much, I added in metacity a command calling your script and indeed it shows the desktop after META+d. But it does not toggle: if I press META+d again nothing happens. I looked in your script and I think the first part of your if condition is never satisfied, because I do not have the /etc/shm directory (what is it?)
Thanks again

---

### Post by 80aless on 2009-10-22
Ok sorry, I got it. I change your /etc/shm/showdesk to ~/showdesk and it works. SOLVED!
Thanks again,
Alex

---

