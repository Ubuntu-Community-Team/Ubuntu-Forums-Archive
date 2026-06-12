---
title: "Lucid Loops on Login"
date: 2011-01-20
forum: Desktop Environments
---

### Post by jbrice on 2011-01-20
This is a mature Lucid installation on an desktop machine. After having to hard reset it after a lockup due to a misbehaving USB peripheral, startup and shutdown started behaving oddly (e.g. shutdown going to a login screen).
Now it is in a state where - on start up - after logging in successfully, the screen goes dark for a moment and then loops back to the login screen.

Have tried:
- booting in recovery mode,
  -- running dpkg repair (just an update of sudo)
  -- running in failsafeX - where problem is still present (so I assume the nvidia video drivers not to blame here)

Maybe relevant that:
- only one user account so cannot try logging in as another user,
- home folder is encrypted.
- hard disk has plenty of spare space.

I'm not sure where to go with this one, so constructive suggestions would be appreciated.

TIA

---

### Post by Krytarik on 2011-01-21
Try the new user thing:

- at the login screen press Alt+Ctrl+F1 and login
- add a new user (with admin rights)
```

sudo useradd NEW_USER
sudo passwd NEW_USER
sudo adduser NEW_USER admin
```- logout and switch back with Alt+Ctrl+F7 or F8
- try to login as the new user

Take a look in ~/.xsession-errors for any valuable error messages.

The same or a slightly different behaviour are experiencing some other people currently.

EDIT: You may also check /var/log/Xorg.0.log.

---

### Post by jbrice on 2011-01-21
Thanks for the quick response Krytarik - really helpful.
I'm not that familiar with Linux at the console level - last time I did stuff regularly at a command prompt it was with CP/M - so your "add new user" instructions saved me a lot of time.

Anyway, new_user account now added sucessfully and logs in just fine (had to add /home/new_user manually, but no problem there). My own log-in ID still bounces back to the log-in screen.

~/.xsession-errors contains:
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/home/****/.gnupg/gpg-agent-info-no6-ubuntu: 1: Syntax error: Unterminated quoted string
```
That doesn't make a lot of sense to me - and file referred to as having a syntax error is presumeably encryted as the text editor shows just random-looking characters in that file.

Where to go from here?

EDIT: renamed ~/.gnupg/gpg-agent-info-no6-ubuntu by adding a ".bak". Can now boot OK and that problematic file has been regenerated and is now readable config text, rather than random chars. Thanks again Krytarik.

---

### Post by Krytarik on 2011-01-21
Fine! Though I don't understand why the home directory of the test user was not created automatically. Could you login or did you have to create the dir before?

---

### Post by jbrice on 2011-01-22
> Fine! Though I don't understand why the home directory of the test user was not created automatically. Could you login or did you have to create the dir before?

When I logged in first time as the new user there were some error messages about being unable to create application configs. etc. But after creating the new user home folder logged in as original user and using sudo, new user login worked fine.

---

### Post by Bo Fussing on 2011-05-12
This issue has been reported as a bug on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574](https://bugs.launchpad.net/ubuntu/+source/gnupg2/+bug/766574)

---

### Post by Patsfriend on 2012-05-28
Hello,
I had same problem. However, NEW_USER login will not show anything Just blank login screen.

How do I add home folder?

Respectfully,
Patsfriend.

> **jbrice said:**
> When I logged in first time as the new user there were some error messages about being unable to create application configs. etc. But after creating the new user home folder logged in as original user and using sudo, new user login worked fine.

---

