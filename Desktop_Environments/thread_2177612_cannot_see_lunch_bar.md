---
title: "cannot see lunch bar"
date: 2013-09-29
forum: Desktop Environments
---

### Post by pouya3 on 2013-09-29
I was trying to work with compiz manager and in the effects part i wanted to have the cube effect, but It offers an option to make bigger Desktop(I dont remember properly)
so i clicked on it and my launch bar is gone, and I couldn't switch between my workspaces, and also failed  to open terminal with shortcuts. How can I return it to default mode?

---

### Post by sandyd on 2013-09-29
> **pouya3 said:**
> I was trying to work with compiz manager and in the effects part i wanted to have the cube effect, but It offers an option to make bigger Desktop(I dont remember properly)
so i clicked on it and my launch bar is gone, and I couldn't switch between my workspaces, and also failed  to open terminal with shortcuts. How can I return it to default mode?

If you can't open a terminal, press Control+Alt+F1

Login,

Install dconf-tools
```

sudo apt-get install dconf-tools
```

Reset Unity and restart unity
```

dconf reset -f /org/compiz/
setsid unity
```

---

