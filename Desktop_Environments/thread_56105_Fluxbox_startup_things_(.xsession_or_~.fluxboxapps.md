---
title: "Fluxbox startup things (.xsession or ~/.fluxbox/apps)"
date: 2005-08-11
forum: Desktop Environments
---

### Post by kzu on 2005-08-11
Neither of these are not working for me, I try to launch my slit apps from there. Here's how my ~/.fluxbox/apps file looks:

[startup] (bbpager &)
[startup] (wmbatteries &)
[startup] (wmcpuload &)
[startup] (wmupmon &)
[startup] (/home/me/.fluxbox/slit/Mixer.app-1.8.0/Mixer.app &)

in ~/.xsession I had:

bbpager &
wmbatteries &
wmcpuload &
wmupmon &
/home/me/.fluxbox/slit/Mixer.app-1.8.0/Mixer.app &

It seems like fluxbox doesn't even read those files, since if I i go to ~ and type ./.xsession slit apps will open :/

---

### Post by Stormy Eyes on 2005-08-11
If you're going to go the ~/.xsession route, you have to select "Default System Session" from GDM's 'Sessions' menu. Make sure that the last line in your ~/.xsession file is "exec /usr/bin/fluxbox". If you want, post the entire contents of your ~/.xsession file and I'll see if there's anything wrong with it.

---

### Post by kzu on 2005-08-11
Thanks, that xsession tip made it work :)

---

### Post by Stormy Eyes on 2005-08-11
No problem. I use .xsession myself, being old-school. It lets me do some heavy customization. If you use OpenOffice.org, I recommend putting the following line in your .xsession:

```
export OOO_FORCE_DESKTOP="gnome"
```

so that OpenOffice.org doesn't look like shit when you start it up in Fluxbox.

---

