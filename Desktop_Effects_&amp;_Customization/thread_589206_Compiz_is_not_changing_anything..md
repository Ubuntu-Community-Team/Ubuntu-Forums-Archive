---
title: "Compiz is not changing anything."
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by spaceship.rodeo on 2007-10-24
I'm stumped here.  Nothing I do seems to be able to change once I make changes in Compiz Settings Manager.  I tried compiz --replace and other such commands, but they don't seem to help.

I'm running Gutsy by the way, and have an Nvidia geforce 7900 with the driver installed.  I frankly have no idea what to do.

---

### Post by craigyjack on 2007-10-24
try doing the command ```
compiz --loose-binding --replace ccp &
```

---

### Post by spaceship.rodeo on 2007-10-24
Well.  Seems to have worked.  Thanks a whole lot.

---

### Post by craigyjack on 2007-10-24
no problems. the ccp part is required for compiz to communicate with compic config settings manager. the default reads your settings from gconf. this seems like it is going to be a big problem for gutsy users, i do not understand why ubuntu did it this way. i see alot of confusion arrising from this, it confused me.
the loose-binding i dont know what it does lol, i just know it supposedly makes it work better if using nVidia driver.

just put that command into your login session commands and away you go.

---

### Post by spaceship.rodeo on 2007-10-24
Right.  What should I use for the name of the command, or does it not matter?

---

### Post by cdekter on 2007-10-25
Somewhere deep down in the Compiz Settings Manager there is a tickbox option that says "Integrate with GConf backend". My guess is, with this enabled, it will write things to the gconf and compiz --replace should do the trick. Maybe you have this option disabled?

---

