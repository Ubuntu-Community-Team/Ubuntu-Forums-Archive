---
title: "Compiz Script Idea"
date: 2007-11-06
forum: Gaming &amp; Leisure
---

### Post by chronusdark on 2007-11-06
I have an idea and if its already made then AWESOME, here it is

what if someone was to make a script that would launch any game given as an argument and disable compiz while the game was running and reenable it when the game was closed

does something like this exist?
could someone make it?

tell me what you think

---

### Post by chronusdark on 2007-11-06
i hate to bump my own thread but does anyone know if something like this exists already?

---

### Post by KuriKai on 2008-03-03
I'm trying to work on one such script now. But am having trouble with replacing compiz with metacity.
The the script to start metacity doesn't stop. so It never moves onto the next part of the script

---

### Post by KuriKai on 2008-03-03
Fixed it
here is my script
```

metacity --replace --sm-disable &
done
exit 0
wine /home/dave/.wine/drive_c/Program\ Files/Warcraft\ III/war3.exe -opengl
compiz --replace --sm-disable --ignore-desktop-hints ccp --loose-binding --indirect-rendering

```
Then I have a link to the script in the gnome panel

---

