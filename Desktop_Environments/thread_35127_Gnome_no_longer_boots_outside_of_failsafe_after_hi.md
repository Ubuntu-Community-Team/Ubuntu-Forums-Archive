---
title: "Gnome no longer boots outside of failsafe after hibernate"
date: 2005-05-17
forum: Desktop Environments
---

### Post by tyraen on 2005-05-17
So I tried hibernation this morning, didn't go so well. The computer just turned off (after a while), and I had to leave for work, so I figured I'd check it when I got home. So now the session ends as soon as I log in unless I choose failsafe. The .xsession-errors file is little help (for me anyways:

[I]/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "nick"
/etc/gdm/Xsession: Beginning session setup...[/I]

And that's the end of it. Anyone experienced any problems like this?

(I also have the Nvidia drivers installed)

Nick

---

