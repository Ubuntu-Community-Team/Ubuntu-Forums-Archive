---
title: "Unity &quot;overlapping&quot; Gnome"
date: 2013-04-08
forum: Desktop Environments
---

### Post by tantocibo on 2013-04-08
Hi people,
I have a big issue: when selecting Gnome Classic from the proper menu in login screen under Ubuntu 12.04, after accessing to desktop, there are both Unity and Gnome showing, at the same time! The Unity Launchbar "overlaps" Gnome menu panel, which becomes totally hidden (the application panel is visible)... That's a strange situation.. Can anyone help me? Here's a screenshot just to show you: [http://goo.gl/MJ2LO](http://goo.gl/MJ2LO)

Thank you.

---

### Post by stinkeye on 2013-04-08
The gnome-classic session uses compiz as the window manager as does the ubuntu session.

Confirm your in the gnome-classic session via terminal...
```
echo $DESKTOP_SESSION
```

Install compizconfig-settings-manager if not installed...
```
sudo apt-get install compizconfig-settings-manager
```
Then run ccsm and disable the unity plugin.
Unlike the other plugins you have to enter the plugin to disable.

---

### Post by tantocibo on 2013-04-10
> **stinkeye said:**
> The gnome-classic session uses compiz as the window manager as does the ubuntu session.

Confirm your in the gnome-classic session via terminal...
```
echo $DESKTOP_SESSION
```

Install compizconfig-settings-manager if not installed...
```
sudo apt-get install compizconfig-settings-manager
```
Then run ccsm and disable the unity plugin.
Unlike the other plugins you have to enter the plugin to disable.

Ok, solved, thank you :)

---

