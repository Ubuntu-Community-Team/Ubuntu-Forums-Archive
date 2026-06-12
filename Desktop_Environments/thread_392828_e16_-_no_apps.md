---
title: "e16 - no apps"
date: 2007-03-25
forum: Desktop Environments
---

### Post by dbbolton on 2007-03-25
at first, i wanted to test e17, but i had trouble with the cvs, so i decided to step down to e16.

for some reason, Synaptic would not let me install package 'enlightenment' or 'enlightenment-data'.
[quote=Synaptic]enlightenment:

Package enlightenment has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list[/quote]

this is a minor inconvenience; i simply download the .debs from the debian website and installed them with gdebi.

i logged in with an e16 session from a simple script i made. (ie, a session without gnome) it works fine, but there are no User Menu's or App Menu's- the left-click menu doesn't work. only the settings and enlightenment menu work.

---

### Post by dbbolton on 2007-03-25
ok, i figured this one out.

when i was trying to install e17, i added an entry at /etc/apt/preferences. deleting this preference allowed me to install e16 via aptitude. then, it included the debian apps menu.

for some reason, the enlightenment session uses the ugly gnome gtk controls, though.

---

### Post by dbbolton on 2007-03-25
ok, so much for that computer.

BUT, on a separate computer, i installed enlightenment from synaptic, and there are no apps ! 

does anyone know the cause of this error ?

---

### Post by dbbolton on 2007-03-26
due to a recent [misfortune](http://ubuntuforums.org/showthread.php?t=393529), i had to reinstall ubuntu on the computer that had e16 working. so, now i have two computers on which the Enlightenment session runs fine, but there is no way to launch applications.

---

### Post by dbbolton on 2007-03-26
ok, i fixed the menu problem by doing this simple operation:

Middle Click (enlightenment menu) > Maintenance > Regenerate Menus

i am *really* surprised than no one could tell me that.

---

### Post by onli on 2007-07-08
Did you had to do anything to get a working middleclick-menu? On my system (dapper) not even the menu appears. I installed it from the repository and there are no error-messages.

Edit: Well, I think my dapper had a problem with update-menu. After I created  ~//.mwm//system.mwmrc-menu, I only had to remove --purge enlightenment and reinstall it. Now everything seems to be fine.

---

