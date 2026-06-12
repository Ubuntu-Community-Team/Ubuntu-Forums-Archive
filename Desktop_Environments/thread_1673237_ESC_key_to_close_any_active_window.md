---
title: "ESC key to close any active window"
date: 2011-01-22
forum: Desktop Environments
---

### Post by Koala Kid on 2011-01-22
Hi good people,
I'd like to set my ESC key to close any active window. Is it possible ?

Thank you :)

---

### Post by ajgreeny on 2011-01-22
Yes, it should be possible in System ->Preferences ->Keyboard Shortcuts, Window management, but it may confuse some programs where the Esc key is already set to do something else, so take care.

---

### Post by Koala Kid on 2011-01-22
Well, you can't really use ESC key, because when you try to set it, it just closes the preferences window :)
What I did is to use this command:
```
wmctrl -c :ACTIVE:
``` and associate it with Alt+Z combination.

---

### Post by ajgreeny on 2011-01-22
> **Koala Kid said:**
> Well, you can't really use ESC key, because when you try to set it, it just closes the preferences window :)
What I did is to use this command:
```
wmctrl -c :ACTIVE:
``` and associate it with Alt+Z combination.
Yes, when you think about it, I suppose it would.

I presume you did get it working OK with no problem, but I'm interested as to why it was needed rather than Alt+F4.

---

### Post by Koala Kid on 2011-01-24
Oh, I wasn't aware of this. Anyway, alt+z is more comfortable for my fingers :)

---

### Post by surfdoc on 2012-07-18
does anyone know if this can be done? i use a mini keyboard (its like using a mobile), so any multi-key function is a hastle. esc is the obvious choice as it is used in programs like xbmc to go back to the parent view.

cheers

---

### Post by surfdoc on 2012-07-18
so the missing link is xbindkeys

install xbindkeys and wmctrl

run

```
xbindkeys --defaults > /home/joe/.xbindkeysrc
```

to create a default config file
edit the file, comment out the examples with #, and add the lines

```
wmctrl -c :ACTIVE:
  Escape
```

then save the file and run

```
xbindkeys
```

voila

---

### Post by |{urse on 2012-07-18
You too cool for alt+f4 or something?

:rolleyes:

edit: oh forum blindness lol

---

### Post by surfdoc on 2012-07-18
Actually - yes :cool:

---

### Post by wildmanne39 on 2012-07-19
Hi, this is an old thread so it has been closed, thanks for sharing.

---

