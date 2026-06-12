---
title: "programs loaded at startup NOT IN /etc/rc?.d"
date: 2009-01-09
forum: General Help
---

### Post by estrel on 2009-01-09
hallo to all,
and good day!

it's some time that i try to wondering why some programs are automatically started up during the boot sequence.
i looked up on google, but all sites suggest that only the programs listed in /etc/rc?.d directory shall start up automatically.
but this is not strictly correct. :confused:
actually, at the boot up, all programs that was already running when i send the sigkill restart. for example pidgin usually is running in background when i power off my pc, and it is running, as well, after a new start up of my pc, without his presence in /etc/rc?.d

is there someone that now WHY? is there an other file linux use to log all programs that were running before shutdown, and that the system automatically restart?

thank you

PS: i'm not english, so i'm sorry if i done some mistake in the text above :( (i hope, and wish, it's understandable too)

---

### Post by blazemore on 2009-01-09
If they start up after you log in, they will be listed in Gnome:
System -> Preferences -> Sessions.

---

### Post by khalidmian on 2009-01-09
Could someone advise me how to enable pidgin and skype to run automatically. What command do i use in session
Thanks

---

### Post by estrel on 2009-01-09
more or less i'm looking at the same, also because of, in the session option, i haven't pidgin listed as automatic startup

---

### Post by Lars Stokholm on 2009-01-09
> **khalidmian said:**
> Could someone advise me how to enable pidgin and skype to run automatically. What command do i use in sessionHave you tried the commands "pidgin" and "skype"?

> **estrel said:**
> more or less i'm looking at the same, also because of, in the session option, i haven't pidgin listed as automatic startupIt sounds like you have "Automatically remember running applications when logging out" checked in the Options tab.

---

### Post by estrel on 2009-01-15
> It sounds like you have "Automatically remember running applications when logging out" checked in the Options tab.

yes, it was...
but i've got linux on my notebook, so i've installed xubuntu.
anyway... i found that option at this path
```
.config/xfce4-session/xfce4-session.rc
```

in that file there's a variable called 
```
SaveOnExit
```
to turn out to false

tanks to all

---

### Post by stefangr1 on 2009-01-15
Programs that are in your /etc/rc.local also start automatically at boot.

---

