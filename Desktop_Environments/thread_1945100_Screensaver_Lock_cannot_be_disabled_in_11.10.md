---
title: "Screensaver Lock cannot be disabled in 11.10"
date: 2012-03-22
forum: Desktop Environments
---

### Post by recluce on 2012-03-22
Since upgrading XUbuntu on my HTPC to 11.10, it seems to be completely impossible to defeat the password lock of XScreensaver 5.14.

This is the scenario:

- "Lock after X min" disabled in Settings / Screensaver
- "Lock Screen on Resume" disabled in Settings / Power Settings
- Screen Lock set to false in ACPI config file

Still, on each resume, there is an XWindows requester (the native, 1980's XWindows style) asking for the password. Annoying. Any ideas to get around this?

System: 32bit Xubuntu 11.10 (upgrade from 11.04 install) with NVidia proprietary drivers on an Intel Atom / Nvidia ION box. Session is XUbuntu.

---

### Post by recluce on 2012-03-24
*** bump ***

Anybody?

---

### Post by Toz on 2012-03-24
Try this from a terminal window:
```
gsettings set org.gnome.desktop.screensaver lock-enabled false
```

Reference: [http://ubuntuforums.org/showthread.php?p=11355285]("http://ubuntuforums.org/showthread.php?p=11355285")

---

### Post by recluce on 2012-04-01
> **Toz said:**
> Try this from a terminal window:
```
gsettings set org.gnome.desktop.screensaver lock-enabled false
```

Reference: [http://ubuntuforums.org/showthread.php?p=11355285]("http://ubuntuforums.org/showthread.php?p=11355285")

Thanks for the idea. Unfortunately, that does not work either.

---

### Post by brainwash on 2012-04-01
Why not just disable XScreenSaver? The XFCE power manager will still put your display to sleep or turn it off.

```
xfconf-query -c xfce4-session -p /startup/screensaver/enabled -n -t bool -s false
```

Now restart the session or kill the current XScreenSaver process.

---

### Post by gmargo on 2012-04-01
Have you checked **$HOME/.xscreensaver**?

It should have a line that reads "lock: False".

Or you could remove that file and reboot, and so you should end up with a new default version of that file.

---

### Post by recluce on 2012-04-08
> **gmargo said:**
> Have you checked **$HOME/.xscreensaver**?

It should have a line that reads "lock: False".

Or you could remove that file and reboot, and so you should end up with a new default version of that file.

I checked, the line "lock: false" is there, but still xscreensaver locks on resume from standby.

---

### Post by Toz on 2012-04-08
Might be a long shot (because its supposed to be deprecated), but in the /etc/default/acpi-support file, there is a LOCK_SCREEN line, Try making the change there (and most probably a reboot will be required). 
> # Comment this out to disable screen locking on resume
LOCK_SCREEN=true

---

### Post by gfisher1 on 2012-04-09
this was a really tough one.  the XFCE power settings password log on disable after suspend is broken.

try this from the account that you are logging on/suspending/resuming:

open a terminal
type:

sudo leafpad /usr/bin/xflock4

change:

   xscreensaver-command -lock

to:

    xscreensaver-command -activate
   
save then reboot

thanks to Tommes for the fix.
[http://www.jogglerwiki.com/forum/viewtopic.php?f=2&t=349&p=7668&hilit=xscreensaver#p7668](http://www.jogglerwiki.com/forum/viewtopic.php?f=2&t=349&p=7668&hilit=xscreensaver#p7668)

works finally for me on xubuntu 32b 11.10 desktop amd a4 3400 ecs a75f-m2 mb.

---

### Post by quadra on 2012-07-06
Thanks, WORKS on xubuntu 12.04 too. Actually I found it better to comment the line out, rather than changing to -activate: less flickering when computer goes to standby. NB reboot wasn't necessary in my case.

---

