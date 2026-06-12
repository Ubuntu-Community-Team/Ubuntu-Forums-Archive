---
title: "Clock"
date: 2006-06-08
forum: Desktop Environments
---

### Post by reyfer on 2006-06-08
Maybe it's a silly question, but why does Kubuntu keep changing my hardware clock to GMT? And how do I stop this behaviour?

---

### Post by scxtt on 2006-06-08
mine acts goofy as well ... i seem to have problems w/ the clock using live cds (i'm running xubuntu right now and the clock is 4 hours fast - as i'm guessing my hardware clock is) - but my installs of breezy and dapper use the correct times ... i ran into problems w/ the clock on installs when i had XP on my computer too ... and when you're installing, the installer asks "are you just using linux" basically saying "if you are, let me set the clock to GMT/UTC and the OS will compensate for your time zone" ... at least that's how i understand it ...

---

### Post by reyfer on 2006-06-08
during install it asked me where I was, but never said it would set the clock to GMT/UTC, I want my clock set to my timezone, My parents use the XP partition, and it's really annoying having to change the clock, and then changing it again when I enter Kubuntu again

---

### Post by Ramses de Norre on 2006-06-08
[CODEgksudo gedit /etc/default/rcS][/CODE]
And set UTC to no.

---

### Post by Jucato on 2006-06-08
He's using Kubuntu, so that should be

```
kdesu kate /etc/default/rcS
```

---

### Post by reyfer on 2006-06-08
@Fenyx and Ramses: THANKS, it worked.

---

