---
title: "Missing Panel"
date: 2007-12-18
forum: Desktop Environments
---

### Post by smartin35 on 2007-12-18
I have been running 6.06 for a few months. Today I decided to update all packages. Once the packages were downloaded and updated I closed the Synaptics Package manager. When I closed the package manager, both the upper and lower panels are missing. Any suggestions for retrieving the panels appreciated.

Thanks

---

### Post by santiagoward2000 on 2007-12-18
Hi there!
Are you using Gnome or Xfce?
If you are in Gnome, try pressing **Alt+F2** and type:
```
gnome-panel
```
For Xfce:
```
xfce4-panel
```

Did that bring them back?

---

### Post by smartin35 on 2007-12-18
I'm in Gnome. When I press Alt+F2, nothing happens. I can press F1 for help and that works. I can also open gedit by clicking on a text file on the desktop, so I know the system is not completely hosed. If I chose to minimize one or both of the applications the windows shrinks down in the right hand corner and disappears from the screen. If I ALT+TAB I can get them to display again.

---

### Post by Nycticorax on 2008-02-02
If you can get a terminal running, then killing the gnome-panel process seems to make the panel reappear (another gnome-panel process is automatically started). To kill the process, type

```
killall gnome-panel
```

I'm having similar issues. In my case when I hide the panel it appears to disappear off the top of the screen, never to be seen again. Anyone know anything about that?

edit: OK so the panel was moving *up* into its hidden position; since it was at the top of the screen that made it disappear. Don't know why it was moving up on hide, but I moved the panel to be at the bottom of the screen and then at least when it moves up into its hidden position you can still see it.

---

