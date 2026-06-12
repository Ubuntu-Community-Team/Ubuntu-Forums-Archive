---
title: "Gnome Schedule Gnome Panel Applet does not work in Natty"
date: 2011-09-07
forum: Desktop Environments
---

### Post by nsk7even on 2011-09-07
Hello,

in Maverick I used the Gnome Schedule Gnome Panel Applet, but now in Natty it does not work anymore.

This is a fresh installation of Natty with all current updates installed.

When adding the Gnome Schedule Applet to the Gnome Panel an error message appears, saying that there were errors when loading »OAFIID:GNOME_GnomeSchedule« and if I want to delete it from configuration.

In syslog there is an error as well:
```
Sep  7 20:12:52 sesta09 bonobo-activation-server (nsk-2283): Passing command-line arguments in .server files is deprecated: "/usr/bin/python /usr/share/gnome-schedule/scheduleapplet.py"
```

In /usr/lib/bonobo/servers I found a GNOME_GnomeSchedule.server file, but I don't understand the relation to the error message as I can not see any command-line arguments in it.

I already tried to deinstall, including removing configuration and reinstall afterwards - but this does not change anything.

Any hints?

7even

//Edit: one - maybe important - thing: I migrated my ~ directory from a backup of the old Maverick system to Natty. Maybe there is an obsolete configuration somewhere? I searched within ~/.config directory already, but found nothing.

---

