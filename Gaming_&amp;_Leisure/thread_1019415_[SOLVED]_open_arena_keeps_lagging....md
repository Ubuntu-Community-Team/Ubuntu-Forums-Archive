---
title: "[SOLVED] open arena keeps lagging..."
date: 2008-12-23
forum: Gaming &amp; Leisure
---

### Post by Dadsgé on 2008-12-23
i've installed openarena, and it works fine :)
till i played like 10 minutes, then the whole game lagges and the game window (which is normally full screen) goes little...
then i cannot do anything anymore, except log-out with ctrl+alt+backspace
this is really annoying..
does anyone know how to solve this problem?

---

### Post by Perfect Storm on 2008-12-23
Does it happen precisly every 10min? If so try disable Screensaver and see if it helps.

Also think of disable compiz to get some more fps.

---

### Post by Dadsgé on 2008-12-23
i haven't tried it yet, but i think this will help ^^
[http://ubuntuforums.org/showthread.php?t=656668](http://ubuntuforums.org/showthread.php?t=656668)

---

### Post by Perfect Storm on 2008-12-23
> **Dadsgé said:**
> i haven't tried it yet, but i think this will help ^^
[http://ubuntuforums.org/showthread.php?t=656668](http://ubuntuforums.org/showthread.php?t=656668)

By disabling compiz, helps in most cases.

Disable;
Gnome
```
metacity --replace
```

KDE
```
kwin --replace
```


Enable;
```
compiz --replace
```


Or installing fusion-icon from synaptic

Or making a launcher script for Open Arena would also make the trick.

---

### Post by Dadsgé on 2008-12-23
hmm, that launcher script would be interesting :p
but how should i write it?

```

metacity --replace
openarena
...
compiz --replace

```

i don't know how to tell the pc that it should do the compiz thing when i ended open arena...

---

### Post by Perfect Storm on 2008-12-23
```
#!/bin/bash 

metacity --replace & 

openarena

compiz --replace &
```


cmod +x the script file.

---

### Post by Dadsgé on 2008-12-23
thanx ^^

---

