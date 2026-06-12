---
title: "Openoffice.org not starting at all in Gutsy"
date: 2007-11-17
forum: Desktop Environments
---

### Post by tonyjazzu on 2007-11-17
Hello there,

Yesterday I've installed a fresh install of Ubuntu Gutsy.

Polish UI for me
Russian for my wife
Lithuanian and english just in case

Language is being selected on the login screen.

Anyway, today openoffice.org stopped starting with a message in lithuanian saying


User interface language cannot be defined.


That's it.

When I uninstalled lithuanian support it showed me the message in english.

Code:
```

sudo apt-get remove openoffice* --purge
sudo apt-get autoremove
sudo apt-get clean

```
And then

Code:
```

sudo apt-get install ubuntu-desktop (contains openoffice + other stuff uninstalled by previous code)
```

Did not help. I went to languages section of system -> administration - it said to add some files, I did it.
Openoffice.org still does nothing...

I thought if I change my default UI language to some other it might work but no. No success at all.
Any hints? But please, if You want to say - uninstall ooo and reinstall - don't unless You have a different way of doing it, one that has proven to help with THIS problem.


Thank You so much for Your time,
Kind regards,
TonyJazzu

---

### Post by aa.ivanov on 2007-11-17
Linux is a true multiuser system. Removing the package does not remove the users' settings for that program. Programs keep these user settings and preferences in hidden directories and/or files under the user home directory. I think removing this directory might help. At least it'll force OOo to start with default settings and defaults are quite robust usually.

Try doing this from a terminal window in the user profile that has experienced the issue:
```
tar -cf ooo-config-backup.tar ~/.openoffice.org2
rm -rf ~/.openoffice.org2
```
This will create an archive with your current settings so you could restore them if you need/like to do so, and then will delete them.

---

### Post by tonyjazzu on 2007-11-17
Thanks!

Unfortunately I got so pissed off that I just created new user, deleted previous - it works. But what's more important - how did the error appear, why did it show me messages in Lithiuanian language, one installed, never used though...

---

### Post by aa.ivanov on 2007-11-19
It's hard for me to say what has happened. And your environment is a bit complex, you know. 

The point is that there are a few different places that set the locale. The global setting for the machine resides in /etc/environment if I'm not mistaken. But this could (and is in your case) overrided by GDM and GNOME per-user-settings. And further more OOo has it's own settings that allow overriding the GNOME settings. 

Anyway it seems like OOo has managed to mess up its configuration. When and how - I don't know. May be it was the messed up configuration that made OOo try loading Lithiuanian... well that was a just wild guess. Hope it'll behave itself this time :)

---

