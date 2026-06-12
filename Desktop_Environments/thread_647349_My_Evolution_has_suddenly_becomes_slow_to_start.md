---
title: "My Evolution has suddenly becomes slow to start"
date: 2007-12-22
forum: Desktop Environments
---

### Post by MikeyXX on 2007-12-22
I use to click the Evolution icon and it would pop up. Now there is a 4 minute pause. I've uninstalled Evolution and reinstalled it with no difference.

This is what I see when I run it from terminal:

michael@michael-laptop:~$ evolution
CalDAV Eplugin starting up ...

** (evolution:6935): WARNING **: LDAP authentication failed (0x51)
evolution-shell-Message: Killing old version of evolution-data-server...
Loading Spamassasin as the default junk plugin
** (evolution:6935): DEBUG: mailto URL command: evolution %s
** (evolution:6935): DEBUG: mailto URL program: evolution

The CalDAV Eplugin starting up... is where it pauses for the greatest length of time, then when it does finally load, the rest appears.


Any suggestion on how I disable either that particular plugin (which is Novell specific) or figure out what's up with that LDAP authentication failure? I don't recall setting up for LDAP authentication.

---

