---
title: "compiz fonts/gtk widgets"
date: 2006-12-17
forum: Desktop Environments
---

### Post by zigford on 2006-12-17
Hey everyone.  With the recent release of new ATI drivers compatible with my Ati Xpress 200m, I can now run XGL/Compiz (Sweet!)

Its running flawlessly and like a champ bar one issue:

Choosing the "Human" theme, corectly displays the window border controls, but not the Human colours.

The Colours are all blue, the gtk widgets seem out of wack and nowhere near as smooth as when I run straight metacity.  Is this how compiz is? or am I doing something wrong?

Check my screenshot and let me know what you think.

[IMG]http://i93.photobucket.com/albums/l64/doc5avage/Screenshot.png[/IMG]

You can see its not Human colours and the gnome-panel "seperator" is much bigger than normal.

Thanks for help

---

### Post by ayoli on 2006-12-18
go to menu System>Preferences>Session
pick Startup programms tab and add:
```
gnome-settings-daemon
```
logout/login
should help

---

### Post by zigford on 2006-12-18
ayoli:  Thank you so much!!
I spent a good bunch of time trying to figure this one on my own.  You got it in one fel swoop.

---

### Post by ayoli on 2006-12-18
glad that helps you :)

---

