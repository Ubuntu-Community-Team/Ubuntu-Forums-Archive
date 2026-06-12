---
title: "Can't log into Gnome!!!"
date: 2006-01-29
forum: Desktop Environments
---

### Post by rozojc on 2006-01-29
Well, a strange thing is happening. One day, out of nowhere, I started having problems logging into Gnome. I start my computer, wait until the login window comes up, type my login name and password, and then I get an error saying either the installation is wrong or I don't have enough space on my hard drive. I know it's not the second, so I suppose that (I don't know why) my Gnome installation just broke (although I can't understand how it would break just becase...).

Anyway, I checked the xsession-errors log and it says the following, if somebody knows how can I fix this I'd be very grateful!

Oh, I forgot, Gnome failsafe doesn't work either. I started terminal safe and I am manually running all the programs (like 'firefox' in order to write to you guys). I'm attaching the log file since it seems I can't copy paste in this type of session.

---

### Post by stevea1210 on 2006-01-29
> ** (gnome-session:9155): WARNING **: Unable to read ICE authority file: /home/familia/.ICEauthority

There is an issue where sometimes the permissions on .ICEauthority get changed.  Looking at the line quoted above, that is may be what happened.  

If you drop to a console (CTRL-ALT-F1), login, then type

```
rm .ICEauthority
```

it will remove the file, and a new one will be created when you log back in.
(CTRL-ALT-F7) to get back to gdm.

Some people suggest reverting the permissions, however I prefer to delete it and get a fresh one.  If you search for .ICEauthority in the forums, you will find many people that have had that issue before.

One of the causes of it seems to be running a KDE app with sudo.

---

### Post by rozojc on 2006-01-29
Solved! thanks

---

### Post by stevea1210 on 2006-01-29
No Problem :-D

---

