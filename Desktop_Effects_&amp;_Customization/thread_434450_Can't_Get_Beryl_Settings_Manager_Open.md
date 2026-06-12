---
title: "Can't Get Beryl Settings Manager Open"
date: 2007-05-05
forum: Desktop Effects &amp; Customization
---

### Post by InuyashaDuelist on 2007-05-05
I've got Beryl up and running, as well as Beryl Manager. Apparently, to get to the Beryl Settings Manager, I'm to right click on the Beryl Manager icon on the task bar, and then click on "Beryl Settings Manager". The only problem is, nothing opens. I've got it installed, as it's visible in Applications -> System Tools -> Beryl Settings Manager.

I'm not sure what exactly the problem is. The effect that comes from attempting to open it from the Beryl Manager, and attempting to open it from the Applications menu is exactly the same - no effect whatsoever.

What can I do? Thanks in advance.

---

### Post by starcraft.man on 2007-05-06
> **InuyashaDuelist said:**
> I've got Beryl up and running, as well as Beryl Manager. Apparently, to get to the Beryl Settings Manager, I'm to right click on the Beryl Manager icon on the task bar, and then click on "Beryl Settings Manager". The only problem is, nothing opens. I've got it installed, as it's visible in Applications -> System Tools -> Beryl Settings Manager.

I'm not sure what exactly the problem is. The effect that comes from attempting to open it from the Beryl Manager, and attempting to open it from the Applications menu is exactly the same - no effect whatsoever.

What can I do? Thanks in advance.

Open the terminal, type in 

```
beryl-settings
```

does the settings manager pop up? If not, what error does it return?

---

### Post by InuyashaDuelist on 2007-05-06
No luck, and the given error message was:

```
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 22, in <module>
    import berylsettings
ImportError: No module named berylsettings
```

---

### Post by InuyashaDuelist on 2007-05-06
Bump.

---

### Post by InuyashaDuelist on 2007-05-07
Bump.

---

### Post by InuyashaDuelist on 2007-06-02
EDIT: Found fix.

I changed the first line of /usr/bin/beryl-settings from "#!/usr/bin/env python" to "#!/usr/bin/python2.5".

---

