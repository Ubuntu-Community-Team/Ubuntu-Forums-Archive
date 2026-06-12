---
title: "Applications open in wrong desktop"
date: 2008-01-14
forum: Desktop Environments
---

### Post by jayph on 2008-01-14
Ubuntu 7.10, fresh install.

My hardware setup:
1 - windows machine with large monitor
1 - linux machine with small monitor (over in the corner)

I want to use some flavor of vnc so I can sit at my windows machine and vnc into the linux machine to use it.

Installing tightvncserver, and editing ~/.vnc/xstartup so that I get a gnome session instead of a black X11 background.

  unset SESSION_MANAGER
  exec gnome-session 

Connect using tight vnc viewer - all is fine - I see gnome on my large monitor.

Start a terminal window, and it opens on the current desktop on large monitor. Open a second (and subsequent) terminal window and it opens on the monitor attached to the linux box.

Make any changes to fonts, apps in toolbars from the desktop in the tight vnc viewer and the changes only appear on the monitor/desktop attached to the linux box.

I've tried every other flavor of vncserver available through the package manager and despite my best efforts they insit on proving me with only a bare-bones X11 desktop.

Please note, I'm not trying to access the local desktop. I know how to do that. The problem is that it is 1280x1024 and I want to use 1920x1200 on the large monitor.

BTW, this all worked fine when I had fedora 6 on the linux box. I decided to update yesterday :(

---

### Post by jayph on 2008-01-14
I was able to get vnc4server running, but it exhibits the same "wrong desktop" behavior, i.e. from the vnc desktop add an item to the toolbar and it shows up on the console desktop instead.

So I'm guessing it has nothing to do with vncserver and something to do with the session manager.

---

