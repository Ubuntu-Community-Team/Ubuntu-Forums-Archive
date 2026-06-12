---
title: "Computer Name Change"
date: 2009-03-04
forum: General Help
---

### Post by gldfshkpr on 2009-03-04
How can I change my computer's name?  I went into System>Admin>Network and changed the name there but in my logs the original name is still there.  I'm having an issue with an app in Wine that requires only alpa/numeric client names and mine has dashes.  It's a network share/app on a Win2003 I'm trying to run.  I've just installed Ubuntu 8.04 so I can re-install if necessary.  I appreciate any suggestions.  I'm new to Ubuntu.

---

### Post by adult swim on 2009-03-04
youll need to change it in /etc/hostname and /etc/hosts

---

### Post by gldfshkpr on 2009-03-04
> **adult swim said:**
> youll need to change it in /etc/hostname and /etc/hosts
Thank you I'll try that tomorrow when I'm at the machine.

---

### Post by gldfshkpr on 2009-03-04
Okay.  That seems to work fine.  I logged in as root and changed those files with gedit.  I still have issues with running the Network app so maybe it has something to do with the way Wine works.  I'll start a new thread.  Thank you.

---

### Post by Halfling Rogue on 2009-04-23
> **asmoore82 said:**
> [SIZE="5"][COLOR="Red"]***Yikes!!***[/COLOR][/SIZE]

you will most likely want to change your hostname through the GUI tools -
it would be under Network preferences -
**especially** if you have multiple location profiles

the NetworkManager Daemon will not honor or preserve manual changes!
(this is the big difference between modern "Desktop" and "Server"
Linuxes - the NetworkMaganer should never be installed on "Servers")

See above.

---

