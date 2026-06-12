---
title: "how do I launch programs as root?"
date: 2005-01-19
forum: Desktop Environments
---

### Post by kdavison007 on 2005-01-19
I can't believe I'm actually asking this question as I've been using linux over a year now, but I ran into a problem the other day when trying to get WiFi Radar to launch as root under the gnome application launcher. 

I right-clicked "add custom launcher" and then for the execution field I put "sudo wifi_radar.py --config"  the sudo messes it up.  It launches fine without that but doesn't get root privs.  When I put the sudo in it doesn't do anything.  I know this works on the CLI fine.  Any help would be great!

---

### Post by DoubleDangerClub on 2005-01-19
To use actual Root, you'll have to set it up on the box you're using.

You'll find this page will be a help in that:

[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root)

---

### Post by Buffalo Soldier on 2005-01-19
[QUOTE=kdavison007]I right-clicked "add custom launcher" and then for the execution field I put "sudo wifi_radar.py --config"  the sudo messes it up.[/QUOTE]

For the execution field try putting in this

```
gksudo wifi_radar.py --config
```

If I'm not mistaken, gksudo is in GUI = sudo is in CLI.

No one knows everything. I have asked a lot of stupid questions myself. But the users here never make me feel ashamed or stupid for asking :)

---

### Post by kdavison007 on 2005-01-19
Thanks!  I haven't posted much on this forum yet, but the information and friendliness I've experienced so far has been incredibly good

---

### Post by DoubleDangerClub on 2005-01-19
[QUOTE=Buffalo Soldier]If I'm not mistaken, gksudo is in GUI = sudo is in CLI.[/QUOTE]

If that works, I'll be a happy camper, I'll try it when I get home.  Oh, and Buffalo Soldier...my mom was born where you live.  Rock. :)

---

### Post by kdavison007 on 2005-01-19
huh.  I tried gksudo and I'm getting the same result.  "gksudo /usr/local/bin/wifi_radar_py --config" still doesn't launch.  Launches if I take the gksudo away, but no superuser privs.

---

### Post by kdavison007 on 2005-01-22
bump for anymore help on this?!- gksudo works on k3b, but not for wifi radar.  Has anyone had an issue with launching a .py file using gksudo?

---

### Post by Buffalo Soldier on 2005-01-23
[QUOTE=DoubleDangerClub]If that works, I'll be a happy camper, I'll try it when I get home.  Oh, and Buffalo Soldier...my mom was born where you live.  Rock. :)[/QUOTE]Kuala Lumpur rocks as hard as other places :)

[QUOTE=kdavison007]bump for anymore help on this?!- gksudo works on k3b, but not for wifi radar. Has anyone had an issue with launching a .py file using gksudo?[/QUOTE]I'll try to look for the solution. Maybe have to do things differently if it's a Python script (.py file). Will get back once I find anything helpful. You can PM me if I forget.

---

### Post by kdavison007 on 2005-01-24
Thanks!  I'll see if I can find anything in the meantime.

---

### Post by kdavison007 on 2005-01-24
Thanks!  I'll see if I can find anything in the meantime.

---

### Post by kdavison007 on 2005-02-03
after some more thinking I found the answer.  If you're using gksudo and the command you're running has switches it's best to put " " around the command.  gksudo thought the --config was a switch for gksudo instead of wifi.  Works great now with gksudo "/usr/local/bin/wifi_radar.py --config"

---

