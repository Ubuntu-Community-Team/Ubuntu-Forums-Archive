---
title: "[SOLVED] Map a key to show desktop"
date: 2006-08-27
forum: Desktop Environments
---

### Post by MikeBenza on 2006-08-27
I'd like to map the Windows key + d to show the desktop.  I'm not even sure where to start looking because I can't search for the phrase "show desktop," only for the individual words.  Can anyone offer some advice?

---

### Post by aysiu on 2006-08-27
Alt-F2 ```
kcontrol
``` Then see the attached screenshot.

---

### Post by w1zard on 2007-05-20
Using Feisty, hitting ALT-F2, then typing kcontrol gives 'File not found'.

The Keyboard Shortcuts application in System->Preferences doesn't let you use the combination of Windows Key and 'D', so it can't be done this way either.

Is kcontrol an optional application I need to install?

---

### Post by guernicaaa on 2007-05-20
> **w1zard said:**
> Using Feisty, hitting ALT-F2, then typing kcontrol gives 'File not found'.

The Keyboard Shortcuts application in System->Preferences doesn't let you use the combination of Windows Key and 'D', so it can't be done this way either.

Is kcontrol an optional application I need to install?

I think it's KDE only because I'm running GNOME and it gives the same message.

---

### Post by DinCahill on 2007-05-20
I don't know about kcontrol, but Beryl has a "Show Desktop" feature, which you could enable if you use it. However, I wouldn't recommend getting Beryl just for that ;)

---

### Post by w1zard on 2007-05-20
I've managed to find out how to do this without kcontrol. This fix was borrowed from another forum posting, and works perfectly. Paste the following into a terminal window:
[FONT="Courier New"]
gconftool-2 -t str --set /apps/metacity/global_keybindings/show_desktop "<Mod4>d"[/FONT]

---

### Post by aysiu on 2007-05-20
KControl is exclusively for KDE, not Gnome (or Kubuntu, not Ubuntu).

---

### Post by lucasdicesaro on 2007-10-02
Show Desktop in Ubuntu: <Control><Alt>d

If you want to see more shortcuts , you cant do this:

1) Alt+F2
2) gconf-editor
3) /->app->metacity->global_keybindings 

More info:
[http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/assign-custom-shortcut-keys-on-ubuntu-linux/)

---

