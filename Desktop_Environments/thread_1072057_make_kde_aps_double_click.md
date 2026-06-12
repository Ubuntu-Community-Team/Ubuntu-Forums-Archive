---
title: "make kde aps double click"
date: 2009-02-17
forum: Desktop Environments
---

### Post by prconnor@gmail.com on 2009-02-17
Hello All,

I have gnome installed, but use a few aps from the kde suite.  I would like to make them behave like my gnome aps; specifically I would like them to be double click.  I prefer not have to install the whole kde suite just to launch the control center and change the behavior to double click.

Is there a config file somewhere where I can make the change?

Thank you

---

### Post by Tim Sharitt on 2009-02-17
What application are you trying to change (konqeror, dolphin, etc)?

---

### Post by yther on 2009-02-17
A quick grep of the files in ~/.kde/share/config suggests you should look at the file "kdeglobals" in there.  Specifically, look for this line:

```
SingleClick=true
```

Try changing it to "false" and see what happens.  (I have mine set that way too, because otherwise I keep accidentally activating things instead of selecting them.)

---

### Post by prconnor@gmail.com on 2009-02-20
> **yther said:**
> A quick grep of the files in ~/.kde/share/config suggests you should look at the file "kdeglobals" in there.  Specifically, look for this line:

```
SingleClick=true
```

Try changing it to "false" and see what happens.  (I have mine set that way too, because otherwise I keep accidentally activating things instead of selecting them.)

This is exactly what I was trying to find.  the kdeglobals file on my system did not have this line.  I added it then launched a kde app.  No luck.  I'm not certain why, but I have checked for typos and believe I didn't misstype it.

---

### Post by gespertino on 2010-07-27
It has to be in the KDE group. Just add:

[KDE]
SingleClick=false

---

