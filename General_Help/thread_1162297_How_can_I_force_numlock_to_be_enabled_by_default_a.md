---
title: "How can I force numlock to be enabled by default after system startup?"
date: 2009-05-17
forum: General Help
---

### Post by kajman on 2009-05-17
I know this isn't a crucial problem... but since I ALWAYS use my numpad for typing in numbers it annoys me a bit, that it disabled by default and every time I try to use it i have to change the numlock setting from off to on.

Any idea how to make it enabled when my system starts?

---

### Post by SuperSonic4 on 2009-05-17
Install numlockx from the repos: ```
sudo apt-get install numlockx
```

Then go to KMenu -> System Settings -> Autostart -> Add Script -> Type in "/usr/bin/numlockx" (without the quotation marks) -> Select when you want it to take effect (mine is at KDE startup which works fine)

---

### Post by kajman on 2009-05-17
Thanks :)

---

### Post by Swatfoot on 2009-05-17
Does this work with Gnome as well ?

---

### Post by SuperSonic4 on 2009-05-18
I think gnome's startup folder is in ~/.Autostart

If you can find gnome's startup folder than it should work but I do not have the means to test it

---

### Post by DLG102282 on 2009-05-18
You dont need to install anything in Gnome it does it automatically after the first time and in KDE you just need to go to the control center click on keyboard and select numberlock on at startup.

---

