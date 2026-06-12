---
title: "gnome-wm delaying login"
date: 2007-06-13
forum: Desktop Environments
---

### Post by brk3 on 2007-06-13
Lately I switched back from beryl to compiz as it seems more stable, however, when I go to login and my desktop is loading up, the splash hangs on the nautilus stage for about 3 minutes and won't load the rest of my startup programs till it is finished.
Ive seen similar posts on the forums that say deleting ~/.gnomerc fixes this but I dont seem to have that file. Ive tried things like deleting all my gnome settings(.gnome2, .metacity, .gconf etc) but nothing seems to work.
Its really frustrating does anyone know why this is happening and how to stop gnome-wm holding up the rest of desktop on startup?

---

### Post by jargoman on 2007-06-15
Hey I have the exact same problem. Sometimes it takes a long time sometimes it doesn't always though the splash screen hanging around and my mouse theme not loading right away. 

Where are these other posts. Can you link them. If I find an answer I'll let you know

---

### Post by macabro22 on 2007-06-18
I also have this issue ={

---

### Post by cor2y on 2007-07-07
Heres the solution i found. After asking in the compiz-fusion and ubuntu and ubuntu-effects irc channel where nobody could help.
Shockingly the solution was hidden away here in the forums.

Anyway.
Launch the gconf editor.
In the terminal its
> gconf-editor
You are going to desktop->gnome-applications->window_manager
change the **default setting**, **not** the current setting, from /usr/bin/compiz
to /usr/bin/metacity 
Then restart x metacity should now boot with no hanging.
The problem with this is when you boot back into xgl is that it may perhaps hang the way gnome did until compiz is launched.

---

