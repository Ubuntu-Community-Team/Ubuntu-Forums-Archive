---
title: "Startup sound in XFCE??"
date: 2005-06-09
forum: Desktop Environments
---

### Post by Kimm on 2005-06-09
I was woundering if it is possible to add a startup sound to XFCE?
so when XFCE has loaded it plays a sound?

---

### Post by felipe on 2005-06-09
not sure if xfce4 has some built-in function for this, but you can always add any command you want in your .xinitrc or .xsession file, just like:

```

exec aplay lame_sound.wav &
exec xfce4-session #not sure this is the right command

```

---

