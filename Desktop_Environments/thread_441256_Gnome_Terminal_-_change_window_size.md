---
title: "Gnome Terminal - change window size?"
date: 2007-05-12
forum: Desktop Environments
---

### Post by itsjustarumour on 2007-05-12
Does anyone know how to get Gnome Terminal to open up with a certain window size?

I'm trying to get it to open at 480x330px to match the background pic I'm using.  I've looked through gconf-editor, but if theres a setting in there then I've failed to find it.

I know its just a tiny little niggly thing-let, but its really bugging me...

Any wisdom gratefully received!  :-)

---

### Post by heimo on 2007-05-12
Have you played with --geometry flag? This seems to give me gnome-terminal close to 480x330(*:
```
gnome-terminal --geometry 59x19
```

*) for text area

---

### Post by itsjustarumour on 2007-05-13
> **heimo said:**
> Have you played with --geometry flag? This seems to give me gnome-terminal close to 480x330(*:
```
gnome-terminal --geometry 59x19
```

*) for text area

Hi Heimo - thanks for that. Right mouse click on launcher, selects "Properties", and then enter that command - just what I was looking for.

Btw - great news about the ice hockey!  :guitar: 

Cheers,

itsjustarumour

---

