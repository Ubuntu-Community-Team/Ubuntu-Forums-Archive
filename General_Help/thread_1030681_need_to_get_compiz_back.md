---
title: "need to get compiz back"
date: 2009-01-04
forum: General Help
---

### Post by Secret Neo on 2009-01-04
compiz was acting funny so i killed the prodcess and iunno how to get it back, anyone help?

edit: i just restarted and its fine but is there any way to get it back when its killed?

---

### Post by stderr on 2009-01-04
Plenty of ways.

```
compiz --replace
```

There's also fusion-icon, which provides a simple blue icon in your system tray. When right clicked, you can switch window managers very simply. 

```
sudo apt-get install fusion-icon
```

You need to start fusion-icon first for the icon to appear; you can do that via Applications -> System Tools -> Compiz Fusion Icon. You can make it start automatically by adding the command 'fusion-icon' as a new Startup Program under System -> Preferences -> Sessions.

oh, and you don't need to kill compiz if it's acting up... you can switch to Metacity via the fusion-icon, or run

```
metacity --replace
```

---

