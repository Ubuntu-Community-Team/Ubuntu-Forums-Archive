---
title: "Unity removed / no main menu shortcut"
date: 2011-12-28
forum: Desktop Environments
---

### Post by bonevg on 2011-12-28
Info:
Ubuntu 11.10 /32 bit (Intel platform)
3.0.0-14-generic-pae
Gnome Version: 2.32.1

Issue:
After removing Unity some main shortcuts havent had key bindings.
Fixed some at: Application -> System Settings -> Keyboard -> Shortcuts.

However, the one that have to open the main menu with ALT+F1 was completely missing from the list of shortcuts.

I can easily add it if I only knew the command, that would open the menu.

Please Advise.
Thank you

---

### Post by bonevg on 2011-12-30
Bump!

---

### Post by grahammechanical on 2011-12-30
You say that you have removed Unity but you do not say what you have replaced it with. Gnome-shell? It is my understanding that Gnome-shell runs on Gnome 3 but you say you have Gnome 2. So, what User Interface are you using?

Regards.

---

### Post by BC59 on 2011-12-30
Look if you can restore the shortcut following this:
[http://ubuntuforums.org/showthread.php?t=1126948](http://ubuntuforums.org/showthread.php?t=1126948)

---

### Post by bonevg on 2012-01-03
> **grahammechanical said:**
> You say that you have removed Unity but you do not say what you have replaced it with. Gnome-shell? It is my understanding that Gnome-shell runs on Gnome 3 but you say you have Gnome 2. So, what User Interface are you using?


* Looks like it is Gnome3 packages all over the place from what
```
 dpkg --list | grep gnome- 
---------------
Example:
---------------
ii  gnome-shell                            3.2.1-0ubuntu1.1                           graphical shell for the GNOME desktop
ii  gnome-session                          3.2.1-0ubuntu1.1                           GNOME Session Manager - GNOME 3 session
ii  gnome-keyring                          3.2.2-0ubuntu0.1                           GNOME keyring services (daemon and tools)
-------
But
-------
ii  gnome-about                            1:2.32.1-0ubuntu6                          The GNOME about box

```

shows.
Assuming the "gnome-about" is leftover package. E.g. package before the dist upgrade.
Not really sure thou, I don't want to sound ridiculous, but it
is what gnome-about is showing.


> **BC59 said:**
> Look if you can restore the shortcut following this:
[http://ubuntuforums.org/showthread.php?t=1126948](http://ubuntuforums.org/showthread.php?t=1126948)
Thank you for the suggestion. The link you gave, helped me to solve the problem.
At first it seemed it doesn't have the option as they explain:

```
7. In the Configuration Editor, navigate to 
apps > gnome_settings_daemon > keybindings"

```
In my case it was:
```

apps > metacity > global_keybindings > panel_main_menu (was disbled)

```
The fix is: change the value of panel_main_menu to: <Alt>F1.
Thank you again
=D>

---

