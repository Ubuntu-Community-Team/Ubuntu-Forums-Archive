---
title: "compiz fusion    missing top bar on all my windows"
date: 2008-12-02
forum: General Help
---

### Post by cowboyup8606 on 2008-12-02
i just installed compiz fusion and now all my top bar tab things  ( where the minimise and maxamize and full screen stuff is ) can anyone hlp me get it back

---

### Post by binbash on 2008-12-02
did you install emerald ? If not install it, then open emerald theme manager (system > preferences) install a theme from gnome-look.org (click import and select .emerald file which you downloaded), select the theme at emerald manager and quit the manager.THen give this command : 

emerald --replace

---

### Post by cowboyup8606 on 2008-12-03
ok i downloaded a theme from gnome-look.org and  installed it but i dont know where to get the the file to import it  ... was i only supposed to save the file to my comp then extract it my self ? or do i have to install this usplash thing ?

---

### Post by Auraomega on 2008-12-03
I had Emerald installed personally, but I had the same problem not so long ago, for a temp fix open the terminal and type Compiz --restart, as long as the terminal is kept open your windows should have the border, plus the ability to move. Bare in mind I did have Emerald installed so it may depend on that to work.

A more permanent fix would be to install the Compiz manager icon thingy (powers of explaination are amazing eh?) You can find it under the package manager if you search for Compiz, but I can't think of the command for apt-get. Once thats installed, set it to run at bootup, and then the icon will be available, just click it, select windows manager and you can choose from what you have, Metacity no doubt.

-Aura

---

### Post by binbash on 2008-12-03
sent you a PM with detailed instructions.

---

### Post by Wartender on 2008-12-03
if not you could just try ```
metacity --replace
```

---

### Post by cowboyup8606 on 2008-12-03
im not using metacity im using compiz

---

### Post by Wartender on 2008-12-03
yes but i have compiz too and i have metacity, i think they're difrerent things, just try it and see what happens (i'm not sure it'll work but by what i've seen around here it should)

---

### Post by ellalan on 2008-12-03
Right click the Fusion icon,select window manager and switch to Metacity then switch back to compiz. Thats what I do whenever this happens to me.

---

