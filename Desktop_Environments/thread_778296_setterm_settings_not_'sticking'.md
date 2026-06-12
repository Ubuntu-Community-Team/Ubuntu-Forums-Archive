---
title: "setterm settings not 'sticking'"
date: 2008-05-01
forum: Desktop Environments
---

### Post by mikeh123 on 2008-05-01
hi,
just a small thing, i want to be able to set the foreground colour of a terminal to red when ssh ing to other machines (just as a warning to myself not to muck about too much).

```
setterm -term linux -foreground red
```

works for the next command, but then reverts immediately back to the default profile.  anyone know how to make this stick so it lasts for the session, so i can ssh in, set the color, then when exit, reverts back ? i don't want to change the .bashrc or .bash_profile on other machines on the network just for this.

this does what i want, but of course in a new xterm window.

```
xterm -fg red -e ssh peters@168.192.2.50 &
```

cheers,
mike.

---

### Post by jshears on 2009-02-17
Guess the reply to this is a little late, but for the benefit of anyone else reading this... you must use the -store option with setterm in order to make the settings "stick"

for example:

setterm -term linux -background black -foreground green -store

will change the terminal to black background and green text and store the settings for the duration of the session. :D

---

### Post by henriquemaia on 2010-10-30
> **jshears said:**
> Guess the reply to this is a little late, but for the benefit of anyone else reading this... you must use the -store option with setterm in order to make the settings "stick"


Well, your reply was still very useful to me, so thanks a lot.

 How do I make the changes permanent reboot-wise?

---

