---
title: "Preventing Shutdown of App"
date: 2005-12-15
forum: Desktop Environments
---

### Post by SuperMike on 2005-12-15
I'm working on an employee timecard kiosk in GNOME with Ubuntu Breezy. I want to either prevent Firefox from being closed or have it reload in the same GNOME session automatically if it is shutdown.

What's the technique to do this?

I've thought out, but haven't implemented, these possible choices:

1) When the system boots up, before the GDM loads, a shell script watches to see if a user "timecard" has logged in by filter on the "w" command. Then, if the user has logged in, if firefox isn't loaded, it does "killall gdm" and "gdm &". It then goes to sleep for 1 minute and wakes up again, in a loop. Since I have my GDM set to automatically login after 30 seconds with the "timecard" user, and since I have a setting already in the timecard profile to automatically fire up Firefox, it will load Firefox again. It's not very clean, however, to have to reload the entire GDM each time. That's what sucks about this idea.

2) I have a shell script that runs automatically inside GNOME when the timecard user logs in. I could have that shell script spawn Firefox and wait in a loop in the background. If it detects that Firefox is shut down, it reloads it again. Perhaps this is the only way to have a script load Firefox within an existing GNOME session.

---

