---
title: "Glmatrix does not display (most of the time)"
date: 2009-01-03
forum: General Help
---

### Post by kesre on 2009-01-03
When I set up GLmatrix to run as screensaver, most of the time, it usually only displays a blank screen.


[edit]: disabling compiz by replacing with metacity solves the problem
```
metacity --replace
```

---

### Post by stderr on 2009-01-04
If you do sometimes use some of the compiz plugins, it can be nice to have an easier way to enable/disable compiz:

```
sudo apt-get install fusion-icon
```

You can then add the command fusion-icon to Startup Programs under System->Preferences->Sessions and (Alt + F2, fusion-icon) to start it. It gives you a small blue icon in your system tray, when right-clicked gives the option to choose your window manger. By default you'll be presented with Compiz and Metacity. 

Alternatively, as you say, just use metacity :) Compiz is rather buggy...

---

