---
title: "I don't want to confirm! (restart/shut down)"
date: 2010-06-12
forum: Desktop Environments
---

### Post by tuxtix on 2010-06-12
I want lucid to restart/shut down immediately. :confused:

---

### Post by moongia on 2010-06-12
> **tuxtix said:**
> I want lucid to restart/shut down immediately. :confused:

Look in power management,under general...thats how i did it with my laptop..now it just turns off with one push of the power button...

---

### Post by wilee-nilee on 2010-06-12
A hard shutdown is not a good thing to be doing!!!!!
Lucid takes about 5-10 seconds to shut down if you put the shutdown button from add to panel instead of using the one that is there with the install.

---

### Post by stinkeye on 2010-06-12
To not have to confirm logout/restart/shutdown...
gconf-editor > /apps/indicator-session/suppress_logout_restart_shutdown

---

### Post by exodus_ on 2010-06-12
If you go to the menu: Systen > Preferences > Power Preferences
then click on the general tab, and the drop-down box for the power button and change it from "ask me" to "shut down" this will enable the behavior you want

---

### Post by drewster1829 on 2011-06-04
Old thread, but I think this is what you're looking for:
[http://blulin.wordpress.com/2010/06/07/disable-shutdown-and-restart-confirmation-dialogs-in-ubuntu-lucid/]("http://blulin.wordpress.com/2010/06/07/disable-shutdown-and-restart-confirmation-dialogs-in-ubuntu-lucid/")

More specifically, go into the terminal (either under Applications>Accesories or hit Ctrl-T), and type (or copy and paste...you can use Ctrl-Shift-V to paste in the terminal window):
```
gconftool-2 &#8211;type bool &#8211;set /apps/indicator-session/suppress_logout_restart_shutdown true
```

This will suppress the confirmation window when using the shutdown menu with the user switcher button in the top right corner of the screen in GNOME, which I assume is what you want.

Edit: And if that didn't work, instead try post #6 [here]("http://ubuntuforums.org/showthread.php?t=1306618"):
> **DeMus said:**
> Type
```
alt+f2
```
In the window that opens then type:
```
gconf-editor
```
Choose in the left column
```
apps, indicator-session 
```
In the right column tick the box which says:
```
suppress-logout-restart-shutdown
```

This last one worked for me in Natty Narwhal with the Ubuntu Classic desktop

---

