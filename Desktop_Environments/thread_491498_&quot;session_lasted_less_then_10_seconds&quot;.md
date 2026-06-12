---
title: "&quot;session lasted less then 10 seconds&quot;"
date: 2007-07-03
forum: Desktop Environments
---

### Post by njofra on 2007-07-03
Can't login (can only to Failsafe terminal) to Gnome on my thinkpad after installing Feisty and other apps for 2 days. Can't remember what was last action, because I was doing many things in parallel. The ~/.xsession-errors file looks like that:
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "njofra"
/etc/gdm/Xsession: Beginning session setup...
x-session-manager: symbol lookup error: /usr/lib/libgnome-2.so.0: undefined symbol: bonobo_activation_get_goption_group

What I've also tried but obviously didn't help:
- checked disk space
- reinstalled libgnome2-0
- reinstalled bonobo-activation
- reinstalled ubuntu-desktop
- reconfigured xserver-xorg

What else can I do/try not to have to reinstall everything? (uninstall libgnome or bonobo means uninstalling other 80-100 packages)

Njofra.

---

### Post by christhemonkey on 2007-07-03
I had a similar problem yesterday, so i left the pc went to bed switched it on this morning and all was well.

So, i dont know, maybe the pc just needs a reboot?!

---

### Post by njofra on 2007-07-03
It's not that simple. I even replaced memory to have 2 identical pieces.

---

### Post by christhemonkey on 2007-07-03
Sorry was just posting as this happened very recently.


Maybe try starting X from htre command line?

```
startx 
```
And post any further errors from there.

---

### Post by Rui Pais on 2007-07-03
> **njofra said:**
> ...
What I've also tried but obviously didn't help:
- checked disk space
- reinstalled libgnome2-0
- reinstalled bonobo-activation
- reinstalled ubuntu-desktop
- reconfigured xserver-xorg

What else can I do/try not to have to reinstall everything? (uninstall libgnome or bonobo means uninstalling other 80-100 packages)

Hi,
Try first detect if it's a problem at system level (broken app or libs) or at user level (broken configuration).

Try to add a new user and check if that happens or not to the new user.

You must add it from a console (Ctrl+Alt+F1) or a failsafe Terminal:
```
sudo adduser new_user
```

Then login as new_user and check how it goes.

---

### Post by sr20ve on 2007-07-03
Have you recently set any new programs to run on startup?

I had an issue like that, I set Desktop Drapes to run on startup, then started getting that error. I went into failsafe and removed that from startup and worked fine.

---

### Post by njofra on 2007-07-03
sr20ve, I'm not aware of any additions to startup, in fact I removed something (think it was hpijs service)
rui, it's the same for all users - no one can log in.

---

