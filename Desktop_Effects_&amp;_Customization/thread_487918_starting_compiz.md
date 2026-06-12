---
title: "starting compiz"
date: 2007-06-29
forum: Desktop Effects &amp; Customization
---

### Post by cawill on 2007-06-29
If I type 'compiz --replace' into terminal, it runs compiz with the effects but with kwin as the window manager, but if I open beryl-manager, select compiz this enables emerald and then put 'compiz --replace' into terminal I get compiz running fully with emerald.

If I run 'compiz --replace' then 'emerald --replace', I then get an error:
/home/chris/.gtk_qt_engine_rc:255: Unable to locate image file in pixmap_path: "22x22/act       { "
/home/chris/.gtk_qt_engine_rc:255: error: scanner: unknown error

(emerald:6650): Wnck-WARNING **: Unhandled action type (nil)


How can this issue be fixed?
Thanks Chris.

---

### Post by dreadlord_chris on 2007-06-29
> **cawill said:**
> If I type 'compiz --replace' into terminal, it runs compiz with the effects but with kwin as the window manager, but if I open beryl-manager, select compiz this enables emerald and then put 'compiz --replace' into terminal I get compiz running fully with emerald.

If I run 'compiz --replace' then 'emerald --replace', I then get an error:
/home/chris/.gtk_qt_engine_rc:255: Unable to locate image file in pixmap_path: "22x22/act       { "
/home/chris/.gtk_qt_engine_rc:255: error: scanner: unknown error

(emerald:6650): Wnck-WARNING **: Unhandled action type (nil)


How can this issue be fixed?
Thanks Chris.

```

compiz --replace -c emerald

```

should work...

---

### Post by cawill on 2007-06-29
It worked, thanks for your help.

---

### Post by hyperair on 2007-06-29
Even so, don't worry about whatever errors the programs tell you unless they don't work. =)

---

