---
title: "Logging out to a text terminal"
date: 2008-06-01
forum: Desktop Environments
---

### Post by Leo Simon on 2008-06-01
I've edited /usr/X11/default-terminal-manager, so that instead of going straight to the GNOME login page on bootup, I now get an old-fashioned text terminal login on bootup.  This means that I can login into FVWM by using startx and avoid the hateful GNOME login interface.   Unfortunately, I have to sometimes access  GNOME, which I do by typing sudo gdm from my text terminal.    In a decent world, logging out of GNOME would take me back to where I started from, i.e., my text terminal.   But it doesn't, it kicks me back to the GNOME login screen.    The only way I now can get back to my text terminal is to reboot.    So my question is:  how can I log out from GNOME and get back to where I started from, i.e., a text terminal?

If possible, please respond to my email address, [email]simon@are.berkeley.edu[/email].
I'm a noob and don't really know how these forums work. 

Thanks Leo

---

### Post by angry_johnnie on 2008-06-01
To get back to text mode from GDM, do this:

press [B]alt + ctrl + F1
[/B]
You'll then be presented with a virtual terminal, where you can log in with your username and password.

Once you're in, do this:

```
sudo /etc/init.d/gdm stop
```

enter your password, and GDM will be gone.

To get back to FVWM, type **startx**, as usual.

---

