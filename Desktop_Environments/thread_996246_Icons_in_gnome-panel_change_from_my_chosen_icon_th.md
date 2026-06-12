---
title: "Icons in gnome-panel change from my chosen icon theme."
date: 2008-11-28
forum: Desktop Environments
---

### Post by kevCast on 2008-11-28
[http://img384.imageshack.us/img384/5629/screenshoteo9.png](http://img384.imageshack.us/img384/5629/screenshoteo9.png)

Anyone know how to fix this?

---

### Post by Giant Speck on 2008-11-29
Well, the first thing you can do is restart the gnome-panel

In a run dialog (Alt+F2), type the following command:

```
killall gnome-panel
```

Press Enter. It should restart itself.  If it doesn't, go back to the run dialog and enter

```
gnome-panel
```

to restart it.


Then come back to let us know if that worked.

---

### Post by Ivo Moelans on 2008-11-29
This probably is a problem of Iceweasel (and Firefox) not adhering to the gtk/gnome guidelines.
I can only speak of Firefox, but since Iceweasel is a derivative of Firefox the principle should be the same.
In Firefox the icons that are used for the windows chooser and in the top left corner of the window are located in */usr/lib/firefox-3.0.4/chrome/icons/default*. There are 3 icons: *default16.png*; *default32.png* & *default48.png*. You probably only need to change *default16.png* (size 16x16 px.) for smaller panels. Of course when you change this to your preferred icon, this also won't change back when you use another icon theme. Also, when a new version is installed you'll have to repeat the process, so, if you decide to do this, it would be handy to keep a copy of the new icon somewhere.
I don't know if this helps.

---

