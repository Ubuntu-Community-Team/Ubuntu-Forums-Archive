---
title: "Restarting X causes weird gnome-settings-daemon problem"
date: 2007-04-24
forum: Desktop Environments
---

### Post by Snowcat on 2007-04-24
Hi!

I have a Feisty Gnome desktop (upgraded from Edgy), and I have an odd problem.
Whenever I restart the X server with CTRL+ALT+Backspace, on the newly started desktop my language applet looks odd (for example, instead of the usual "USA" appears "us"), and clicking on "Keyboard Preferences" causes the following error to appear:

```
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```

But then the settings screen does appear.
I don't know what happens if I try to change something and save it, as I'm afraid of breaking something (and everything works fine when I first boot the computer, so I can change my preferences then).

This isn't a terribly major bug, but I would love to find a way to resolve it anyway.
All help would be appreciated.

---

### Post by c4pp4 on 2007-05-04
I had the same problem, when Gnome started after boot, everything worked fine, but when I logged out and logged in, [COLOR="Blue"]language applet[/COLOR] showed "us" and "cz" instead of "USA" and "&#268;es", and [COLOR="Blue"]trash applet[/COLOR] didn't work, it always showed empty trash although I had some files deleted.
I resolved it editing file:
```
sudo nano -w /etc/gdm/Init/Default
```
before the final **exit 0** I added **evolution --force-shutdown**
Now I don't have a problem with it.
It's not clean solution but maybe it helps you too.
I think that there is something wrong with evolution but I'm not sure what kind of bug it is...

---

### Post by Snowcat on 2007-05-09
Yay, it worked! Thank you so much! \\:D/ 
I wonder how evolution (which I never use at all) causes this...

---

