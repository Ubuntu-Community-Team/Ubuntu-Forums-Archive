---
title: "Gnome Panel messed up after repairing broken Firefox"
date: 2009-06-10
forum: Desktop Environments
---

### Post by densou on 2009-06-10
I was not aware of broken FF 3.0.10 so I had to fix it by myself [a complete purge and re-install]

The next day, FF worked well but I noticed Gnome Panel had issues with menu's translation : some lines had right localization and the remaining ones were stuck into English (but I'm NOT the only user of this desktop so I need to have the full localization asap  :o ]

already tried:
*updating GNOME from PPAs* [not from scratch, it always fail 'make' or 'install' when I try -_- ]
*another kernel*
*set LC_ALL LANG LANGUAGE into /etc/environment*
*dpkg-reconfigure locales* (I still have *us.US UTF-8* in the first line of terminal output, I erased the right folder in Nautilius but nothing happened)


any clue ????

:confused:](*,)[-o<

---

### Post by densou on 2009-06-11
bump :(

---

### Post by psyke83 on 2009-06-11
Before you proceed, create a new user account, log in to that new user's account, and see if the panel is working correctly.

If it works correctly for the new account, it's likely that have a problem with your panel's user configuration - resetting the settings should help.

You can reset the panel configuration by removing the following folders:
```
~/.gconf/apps/panel
~/.gnome2/panel2.d
```

BACKUP these files/folders before deleting.

I also don't recommend that you use third-party packages/builds for the panel, keep everything to defaults.

---

### Post by densou on 2009-06-12
thanks lad/mate,
already tried your advice yesterday and nothing happened. ;)

I tried also to restore GNOME default packages (deleted actual configuration after a backup) but :(

---

