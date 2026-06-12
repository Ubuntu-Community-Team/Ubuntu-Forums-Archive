---
title: "gnome-terminal fails to start with timeout"
date: 2017-11-14
forum: Desktop Environments
---

### Post by rpgoldman2 on 2017-11-14
After a recent ```
sudo aptitude safe-upgrade
```, I am no longer able to run ```
gnome-terminal
```.

I find this error:
```
Error constructing proxy for org.gnome.Terminal:/org/gnome/Terminal/Factory0: Error calling StartServiceByName for org.gnome.Terminal: Timeout was reached

```

I *believe *that ```
gnome-terminal-server
``` is not operating.

I have read several posts about this being due to locale problems, but although I have made the locale repairs suggested, gnome-terminal still won't start.  Here's the output of ```
localectl
```:

```

$ localectl
   System Locale: LANG=en_US.utf8
       VC Keymap: n/a
      X11 Layout: us
       X11 Model: pc105

```

I have no idea why the VC Keymap is not set.

Note, I am trying to do this over a VNC connection.

Thanks for any help!

---

### Post by anshumankmr on 2018-08-22
Hello sir, 
I know it might be very late but were you able to find a solution to your problem?? Please share it as I need help myself.

---

### Post by wildmanne39 on 2018-08-22
Hello and welcome to the forum anshumankmr, please start your own thread if you need help and do not post in someone else's you will be more likely to get the help you need that way.

---

