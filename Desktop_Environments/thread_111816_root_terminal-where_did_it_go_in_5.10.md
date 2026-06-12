---
title: "root terminal-where did it go in 5.10"
date: 2006-01-03
forum: Desktop Environments
---

### Post by mjezell on 2006-01-03
hi,

i've been using ubuntu for about a year now and we've been get along just find. Along comes 5.10 and and i want to upgrade but i can't find the root terminal. i don't want to sudo i like using the terminal as root. Tried konsole but you don't get root privilages with it. it's probably right under my nose but i've been looking for it for several months and thought i might need some help. thanks to anyone that is willing to spend the time on this.

regards,
mike

---

### Post by diffuser78 on 2006-01-03
Your substitute for the time being is 
```

sudo -s -H

```

[QUOTE=mjezell]hi,

i've been using ubuntu for about a year now and we've been get along just find. Along comes 5.10 and and i want to upgrade but i can't find the root terminal. i don't want to sudo i like using the terminal as root. Tried konsole but you don't get root privilages with it. it's probably right under my nose but i've been looking for it for several months and thought i might need some help. thanks to anyone that is willing to spend the time on this.

regards,
mike[/QUOTE]

---

### Post by bornagainubuntist on 2006-01-03
Fire up the menu editor:

System Tools > Applications Menu Editor

Click on System Tools in the left pane, then tick Root Terminal in the right pane.  You should now be able to get a root terminal by naviagting to System Tools > Root Terminal.

---

