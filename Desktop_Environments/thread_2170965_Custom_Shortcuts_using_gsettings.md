---
title: "Custom Shortcuts using gsettings ?"
date: 2013-08-28
forum: Desktop Environments
---

### Post by serg2 on 2013-08-28
Hi, I am running on 12.04 with default Unity, and I have found that all my custom shortcuts are getting reset after every reboot(looks like bug), - honestly annoying.  
I am trying to setup that keys into /etc/rc.local so after reboot it will be set automatically.  
I found that custom shortcuts could be set using "gsettings set <schema> <shortcut name> <action> <bind_keys>"  However I cannot find what schema should be used for custom shortcuts?  
Or may be you know another way how to solve this issue? Any inputs are welcome.

---

### Post by serg2 on 2013-08-28
well, I found that custom shortcuts could be set using this commands:

$ gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ name "custscut"
$ gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ command "~/bin/cmds.sh"
$ gsettings set org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ binding "<Super>X"


however my issue is that the path  org.gnome.settings-daemon.plugins.media-keys.custom-keybinding doesn't exist on my installation:
$ gsettings get org.gnome.settings-daemon.plugins.media-keys.custom-keybinding custscut
No such schema 'org.gnome.settings-daemon.plugins.media-keys.custom-keybinding'

$ gsettings get org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ custscut
No such schema 'org.gnome.settings-daemon.plugins.media-keys.custom-keybinding'





$ dconf list /org/gnome/settings-daemon/plugins/media-keys/
calculator
screensaver

openning dconf-editor i dont see custom-keybinding path either. Why it is missing? And where my shortcuts stored that were created through System -> Keyboard -> Shortcusts -> Custom Shortcuts ?

---

### Post by mc4man on 2013-08-28
> **serg2 said:**
>  And where my shortcuts stored that were created through System -> Keyboard -> Shortcusts -> Custom Shortcuts ?
In gconf (gconf-editor
/desktop/gnome/keybindings/

---

### Post by serg2 on 2013-08-29
thanks, but how they could be added every time after reboot? is it possible using gsettings? or any other commands?

---

### Post by mc4man on 2013-08-29
Well the bindings could be set with a gconftool command but there are up to 3 per custom command
(- name, action (command), binding

So what is being unset? (all 3, or just the binding

As I remember there have been some continuing issues with bindings being unset though it is much improved in 13.04/10
( though I can't exactly recommend either at this point

Could you give an example of one or at the least what bindings you're using
(some binding may be more likely to be unset on a restart.

In any event I found this page, which while for something else,  gives you some  idea of the 3 actual commands per custom shortcut
[http://www.heath-bar.com/blog/?p=592](http://www.heath-bar.com/blog/?p=592)

If nothing is being unset but instead the binding stops working then you may need to construct some sort of 'toogle' script, ie.,  sets the binding to either nothing or something else, then resets to your intended one

---

### Post by serg2 on 2013-08-30
thanks a lot, the solution with using "gconftool-2 --set" works for me, and I was able to create a script that re-enables shortcuts on reboot.

---

