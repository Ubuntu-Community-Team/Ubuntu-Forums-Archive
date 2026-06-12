---
title: "Missing all my applications - Ubuntu 11.10/Unity"
date: 2011-11-14
forum: Desktop Environments
---

### Post by ricardof84 on 2011-11-14
Hey,

I'm having the weirdest issue here. I upgraded to Ubuntu 11.10 recently (using Unity on a Dell betbook) , everything up to date, no issues and all of a sudden i rebooted normally and now all my apps are missing. I can't even find the terminal by doing a search... I cant find any of my apps.

Everythign else is fine, i can open Openoffice apps and firefox (because they are docked in the left tool bar), but i cant find the rest of the apps.

Looks like something that can easily be fix, but im wondering if its something that happens frequently and theres a quick fix ?

---

### Post by BillyBoa on 2011-11-14
To open a terminal CTRL+ALT+T

Then try to do a Unity icons reset:

```
unity --reset-icons
```

or a Unity reset:

```
unity --reset
```

---

### Post by ricardof84 on 2011-11-14
Thanks BillyBoa. I'll try this and let you know how it turns out. =)

---

### Post by ricardof84 on 2011-11-15
i did a 'unity --reset' but in the terminal i keep getting errors that im missing some lenses and then finally it stops on a message asking me to report the bug if reinstalling the lenses does not work.

ERROR : "compiz (core) - Warn: failed to receive ConfigureNotify event on 0x4400044

WARN 2011-11-14 19:13:30 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN 2011-11-14 19:13:30 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
compiz (core) - Warn: unhandled ConfigureNotify on 0x1000095!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
I use 64-bit ubuntu onoric, and this happened after update."

FYI - I tried the instructions in this link : [http://askubuntu.com/questions/43096/unity-lenses-missing-files-folders-applications](http://askubuntu.com/questions/43096/unity-lenses-missing-files-folders-applications)

Also, if i dont close the terminal running the unity reset, i get all my apps back, i can do a search in dash and everything is back to normal, but once i restart my pc everything gets screwed again.

---

### Post by raja.genupula on 2011-11-15
reinstall unity from software center , that may gonna help you to solve the issue.

all the best.

---

### Post by Frogs Hair on 2011-11-15
Some applications you may have used may not be Gnome 3 compatible , so if you are able to restore the panel some installation my be required .

---

### Post by ricardof84 on 2011-11-17
Things got even worse. I couldn't even see history in my firefox browser, use the back button, or any other app that stored temp data.

I just created a new user and deleted the old one. Everything is now ok with the new user. I guess its not a system issue, it has to do with something that i screwed up in the desktop config i don't have a clue on what could that have been... I didnt intend to change anything...

---

