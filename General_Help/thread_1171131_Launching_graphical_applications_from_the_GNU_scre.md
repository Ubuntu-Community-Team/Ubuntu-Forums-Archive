---
title: "Launching graphical applications from the GNU screen utility?"
date: 2009-05-27
forum: General Help
---

### Post by Vunutus on 2009-05-27
Obviously the purpose of GNU screen is not graphical applications, but I want to have a script running inside screen that is able to launch a Zenity dialog. Is this even possible at all? I searched around and didn't find any information.

Every time I try to launch a zenity window inside screen (with a line that works fine if I just paste it in a normal terminal), I get this error:

```
(zenity:21744): Gtk-WARNING **: cannot open display:
```

Obviously this means that zenity cannot interact with GTK, but I have no idea how to fix it (or if it even can be fixed).

---

### Post by iiska on 2009-05-27
If you are running the screen on a local computer, set the environment variable DISPLAY to refer your X display, when launching the app.

$ DISPLAY=":0.0" some-x-app

If screen is on some remote machine use -X parameter with ssh, and DISPLAY should be set automatically.

---

