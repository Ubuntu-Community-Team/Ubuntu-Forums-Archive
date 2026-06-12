---
title: "Compiz not starting on bootup?"
date: 2009-02-05
forum: General Help
---

### Post by gbrethen on 2009-02-05
This was working, now when I boot up, compiz does not start automatically.  I have to right click on the fusion icon in the system tray and click on 'reload window manager' for it to start?  The only thing that has changed, is that my startup session was changed from 'Xclient script' to 'Gnome'?

Help!!!

---

### Post by gettinoriginal on 2009-02-05
Go into terminal and type:  :p
```
compiz --replace
```

---

### Post by gbrethen on 2009-02-05
now, how do I get it to start at bootup everytime without typing that into a terminal?

---

### Post by gettinoriginal on 2009-02-05
System, Preferences, Sessions, Add, name it (Compiz?), command "compiz --replace",(without quotes), select Add at bottom.

---

### Post by RedSingularity on 2009-02-05
System>Preferences>CompizConfig Settings Manager>Effects>Window Decoration||||  Then by COMMAND type compiz --replace.

Edit: Wooooo i am too slow!^^^   x_x

---

### Post by pbotros1234 on 2009-02-05
The above method with "compiz --replace" might be a slower load time, because that means that the default window manager (metacity) will load first, and then compiz will load, replacing it.

Use the XClient script instead, it should work better. This way, compiz loads straight-up and metacity doesn't have to load.

Not too sure about this, but worth a try.

---

