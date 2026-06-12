---
title: "Getting Ubuntu back from Edubuntu!"
date: 2013-05-03
forum: Desktop Environments
---

### Post by MrMichaelHill on 2013-05-03
Been googling this for ages now!

As an IT Tech in education I was curious about the package 'educational bundle' in software centre, thought it would be a collection of kids games and programs I could test. turns out its change half of my bloody 12.04 OS!

The Dash Home button is Edubuntu, the login screen Says Edubuntu and my boot up splash screen says Edubuntu! :(

I want my Ubuntu 12.04 back to normal please :(:(

Thanks!

---

### Post by grahammechanical on 2013-05-03
Are you sure that it was not Educational Desktop for Ubuntu that you installed instead of either Pre-school bundle, Primary Bundle, Secondary Bundle and Tertiary Bundle?

Software Centre usually gives us an option to remove packages that we install through the Centre. Are you not getting that option?

Regards.

---

### Post by lykwydchykyn on 2013-05-03
These terminal commands may do it:
```

sudo apt-get purge edubuntu-desktop && sudo apt-get autoremove

```

---

### Post by MrMichaelHill on 2013-05-03
Right! Managed to sort it in the end,

I removed all the obvious stuff first like 'Edubuntu desktop for Ubuntu' then I went to 'More info' listed all the packages like fonts and edubuntu themes, then searched for them seperately in software center and removed.

All is well again now ;)

Thanks!

---

