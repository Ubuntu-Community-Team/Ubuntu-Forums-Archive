---
title: "Disable auto lock-screen in a laptop"
date: 2005-11-18
forum: Desktop Environments
---

### Post by deigote on 2005-11-18
Hi! I've got a Toshiba Satellite L20 101. When I close the screen, it gets locked automatically, so when I open it again I must introduce the password. I find this a littlebit annoying (maybe bad written, sorry for the english). I've disabled all screensaver features (including the energy administration) and still happens. Does any one knows how to turn this off? Thanks a lot.

---

### Post by giftnudel on 2005-11-23
Hi,

check /usr/share/acpi-support/screenblank and change the line:
su $user -c "(xscreensaver-command -throttle; xscreensaver-command -lock)"
to su $user -c "(xscreensaver-command -throttle)"
I know this is late, but now at least people can search for it

giftnudel

---

### Post by ranf on 2005-11-23
[QUOTE=deigote]Hi! I've got a Toshiba Satellite L20 101. When I close the screen, it gets locked automatically, so when I open it again I must introduce the password. I find this a littlebit annoying (maybe bad written, sorry for the english). I've disabled all screensaver features (including the energy administration) and still happens. Does any one knows how to turn this off? Thanks a lot.[/QUOTE]
I think the best place to set it up the way you want is to edit `/etc/default/acpi-support'. 
There you will find these lines:
```
# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

```

---

### Post by giftnudel on 2005-11-23
Hi,

note that this only works on resume and not on lid close (at least as far as I can tell from the scripts, on lid close, this variable is not checked). It actually should, so I will file a bug ...
giftnudel

---

### Post by ranf on 2005-11-23
[QUOTE=giftnudel]note that this only works on resume and not on lid close (at least as far as I can tell from the scripts, on lid close, this variable is not checked). It actually should, so I will file a bug ...
[/QUOTE]
Ok. Haven't looked that much into it.

---

