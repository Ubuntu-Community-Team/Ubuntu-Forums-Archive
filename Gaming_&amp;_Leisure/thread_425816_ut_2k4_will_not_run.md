---
title: "ut 2k4 will not run"
date: 2007-04-27
forum: Gaming &amp; Leisure
---

### Post by endo666 on 2007-04-27
i got ut 2k4 installed but when i start the program the splash screen for the game pops up but then it disappears and the game dose not start.

---

### Post by handy on 2007-04-28
> **endo666 said:**
> i got ut 2k4 installed but when i start the program the splash screen for the game pops up but then it disappears and the game dose not start.

Do you have a 3D graphics card installed with the restricted drivers i.e. an ATI or hopfully an nVidia card?

Also, I think if you read in the manual it will give you a command to start the game in safe mode.

Some help I hope? :)

---

### Post by endo666 on 2007-04-28
i have no clue. i have and ati card. the x1300 pro. and rite now i have no clue where i put the manual.

---

### Post by handy on 2007-04-28
> **endo666 said:**
> i have no clue. i have and ati card. the x1300 pro. and rite now i have no clue where i put the manual.

On my install, I find the manual in the install directory:

***handy/ut2004/Help/Readme.int.txt***

Have a search of the forums for your card, & see what you find out, I don't know it, but that means nothing :-)

---

### Post by BlueStreak on 2007-04-28
Had the same problem, it ended up being a permissions problem.  I gave myself full access to .ut2004 in my home directory then everything worked fine.  Hope that helps

---

### Post by Cappy on 2007-04-28
like so:
```

sudo chown -R yourusername:yourusername ~/.ut2004/

```
The -R makes it recursive for ALL of your personal .ut2004 files.

Try running "ut2004" in a console and see what error msg you get.

---

### Post by handy on 2007-04-28
Not having strong 3D will also cause major problems.  Though it is possible to run with software rendering, you would want a strong machine & low graphics quality setttings for it to be playable.  Probably a waste of time for LAN/internet play though.

---

