---
title: "LOL beryl white screen problem + startup issue"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by Apocrathia on 2007-08-23
okay so heres a dumbass mistake i made, i just setup an ubuntu partition on my primary computer. and on the last one i did i set beryl to run at startup (via the sessions menu).
okay so beryl's giving me the white screen of nothingness. the cube and all still works, but its white on all 4 sides with the gems on the top and bottom, lol.
so how can i either A) remove beryl from the startup from the console or any other possible way, or B) fix the white screen problem.
thanks

EDIT:

nvm, i fixed the problem.
i just booted failsafe and ran
```
sudo apt-get remove 'beryl*'
```
that uninstalled beryl allowing me to access the sessions manager, and i removed the beryl startup item.
problem with the white screen is that i forgot to install my nvidia drivers. lol
hope this mistake helps someone
btw, if that happens to you, ive seen it called the beryl white screen of death. kinda funny side note.

---

### Post by jakev383 on 2007-08-23
I was going to ask if you had installed the drivers - I had the same thing happen with my nvidia card. I enabled the restricted drivers, and no issue afterwards.

To get good at fixing something, you need to first be good at breaking it, eh?

---

