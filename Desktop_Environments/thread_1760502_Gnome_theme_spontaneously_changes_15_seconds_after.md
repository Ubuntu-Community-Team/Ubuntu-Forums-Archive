---
title: "Gnome theme spontaneously changes 15 seconds after login"
date: 2011-05-17
forum: Desktop Environments
---

### Post by deep42thought42 on 2011-05-17
I recently upgraded from Ubuntu 10.10 to 11.04. My hardware can't support fancy effects, so I'm using the "Classic (no effects)" desktop.
When I logged in, all programs would be themed in one way, then 15 seconds later everything would change to a different theme. Neither of these themes was the theme that I had selected in the configuration. I came here to ask for advice, but discovered this first:

[http://www.romaco.ca/blog/2011/02/20/how-to-fix-gnome-theme-problems-with-ubuntu/](http://www.romaco.ca/blog/2011/02/20/how-to-fix-gnome-theme-problems-with-ubuntu/)

Summary:
gnome-settings-daemon has a race condition that is triggered if it starts too fast.
Workaround:
in
/etc/xdg/autostart/gnome-settings-daemon.desktop
change
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
to
Exec=bash -c 'sleep 2;exec /usr/lib/gnome-settings-daemon/gnome-settings-daemon'

---

### Post by wildmanne39 on 2011-05-17
> **deep42thought42 said:**
> I recently upgraded from Ubuntu 10.10 to 11.04. My hardware can't support fancy effects, so I'm using the "Classic (no effects)" desktop.
When I logged in, all programs would be themed in one way, then 15 seconds later everything would change to a different theme. Neither of these themes was the theme that I had selected in the configuration. I came here to ask for advice, but discovered this first:

[http://www.romaco.ca/blog/2011/02/20/how-to-fix-gnome-theme-problems-with-ubuntu/](http://www.romaco.ca/blog/2011/02/20/how-to-fix-gnome-theme-problems-with-ubuntu/)

Summary:
gnome-settings-daemon has a race condition that is triggered if it starts too fast.
Workaround:
in
/etc/xdg/autostart/gnome-settings-daemon.desktop
change
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
to
Exec=bash -c 'sleep 2;exec /usr/lib/gnome-settings-daemon/gnome-settings-daemon'
Hi, would you please post here how you fixed the problem in case other people might have the same problem. Thank you.:D

---

