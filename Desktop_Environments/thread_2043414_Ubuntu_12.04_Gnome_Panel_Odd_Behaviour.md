---
title: "Ubuntu 12.04 Gnome Panel Odd Behaviour"
date: 2012-08-16
forum: Desktop Environments
---

### Post by cryptotheslow on 2012-08-16
Hi,

I installed gnome panel on a standard Ubuntu 12.04 install as per this sticky thread:
[http://ubuntuforums.org/showthread.php?t=1859961](http://ubuntuforums.org/showthread.php?t=1859961)

On first login to it, it behaved perfectly - and distinctly snappier opening applications.

However, I logged back into a Unity session and then back into the Gnome Classic session and it is now quite broken. The Gnome bottom panel is still present, but so is the Unity launcher and the global menus (obscuring where the Gnome desktop menus would be on the top panel).

Logging back into Unity subsequently then apeared as though a unity-reset had been done - everything back to defaults. Easy enough to fix but it happens every time I use the Gnome Clasic session.

Anyone else come across this and know how to fix it?
Is it just a case of fixing up the Gnome Classic session again and then never ever logging into Unity again?

Thanks :)

---

### Post by cryptotheslow on 2012-08-16
OK - I have sort of cleaned this up.

Login to the Gnome Classic session and use a terminal to:

1. Reset Gnome Panel using dconf-tools:
```
sudo apt-get dconf-tools
dconf reset -f /org/gnome/gnome-panel
killall gnome-panel
```

That seems to sort it until you open an application and the global menus come back.

2. Disable the Unity compiz plugin:
a. I installed Compiz Configurations Settings Manager (CCSM) using Synaptic but you code just as well:
```
sudo apt-get install compizconfig-settings-manager
```
b. Use that to disable the Unity plugin.

OK - now the launcher has gone along with the global menus obscuring the gnome panel.

However - some key bindings are still missing, such as Alt-Tab is now non-functional.

One more test to do.......  run a Unity session and see if this all gets undone.

---

### Post by cryptotheslow on 2012-08-16
Sooo... tried to run a normal Unity session - and no top panel and no launcher.

Ran CCSM from a terminal (Ctrl-Alt-T) and the Unity plugin has no checkbox present to re-enable it.

Back to Gnome Panel and things are still mostly OK (key bindings still messed up).

I can only conclude Unity and Gnome Panel are not happy bedfellows and suggest if you want to use Gnome Panel, by all means install it and use it but **never ever** log back into a Unity (Ubuntu) session again, do not look back :D

Now just to work out how to fix my key bindings.

---

### Post by cryptotheslow on 2012-08-16
And back in Unity - still no Unity.

Did a:
```
unity --reset
```

10 minutes later, the launcher and panel had reappeared but not much else working.

So moved to tty1 (ctrl-alt-F1):
```
sudo service lightdm restart
```

All is back to normal again in the Unity session albeit with default settings.

I guess Gnome Panel and Unity have very conflicting compiz configurations so it is a one or the other deal. Happy to be corrected on that :D

---

### Post by PaulInBHC on 2012-08-16
There are a few threads about people losing the launcher and panel and nothing seems to help. I'll try what you did but I don't have much hope.

---

