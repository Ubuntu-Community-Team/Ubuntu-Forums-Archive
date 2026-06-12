---
title: "Launch application &quot;Always Below&quot;, Undecorated"
date: 2011-09-04
forum: Desktop Environments
---

### Post by ManualSparrow on 2011-09-04
Hello,
I'd like to launch a terminal on startup that would "live" on the desktop background, kind of like widgets in KDE or conky. Is there a startup option in xfwm4 that would allow me to launch an application using the "always below" option available if you click on a window decoration? xfterm4 -below doesn't seem to be an option.
-Thanks

---

### Post by hhh on 2011-09-04
For one thing, the terminal in Xfce is xfce4-terminal, not xterm4, AFAIK. For another, I see an "Always on top" option but not "always below" when clicking a title bar. third, man xfce4-terminal isn't showing me any good options there. But I never looked into this as it doesn't seem a big deal to me to just open a terminal when necessary, or open it first thing in a session and minimize it.

that said, what about trying one of the "panel" terminals like Tilde,  Guake or Yakuake?

---

### Post by ajgreeny on 2011-09-04
Install alltray and then start terminal with command```
alltray xfce4-terminal
``` in your startup applications list, wherever that is in xfce4.  It should start with no window, but still open as just an icon in the panel, if it works the same in xfce as it does in gnome.

This is not quite what you asked for, but nearly.

---

### Post by Toz on 2011-09-04
As an alternative to the two mentioned options above, Devil's Pie should also be able to do this for you.

[http://burtonini.com/blog/computers/devilspie/]("http://burtonini.com/blog/computers/devilspie/")
[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/]("http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/")
[http://www.foosel.org/linux/devilspie]("http://www.foosel.org/linux/devilspie")

---

### Post by ManualSparrow on 2011-09-05
Thank you for the suggestions. 

In the past I have used Guake and Yakuake, but I am trying to avoid installing a bunch of packages if I can just append a simple condition to a command. Plus, if such an option existed, I could use it to output a simple calendar alongside the terminal and use show-desktop as a kind of organizational home screen. 

For now I suppose I'll just stick with conky monitors.

EDIT: Devil's Pie will do all that, it seems. Thanks!

---

