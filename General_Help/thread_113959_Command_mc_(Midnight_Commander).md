---
title: "Command: mc (Midnight Commander)"
date: 2006-01-07
forum: General Help
---

### Post by rensu on 2006-01-07
Can anyone tell me what's wrong with my mc. The display is pretty messed up with different foreign letters.

---

### Post by duminas on 2006-01-07
A screen capture may help.
My idea would be that you're using an odd font for your terminal. Are you using the default terminal application (gnome-terminal), or no? If no, which? The font issue might be arising from your locale. Most obviously, try to use the default Terminal application that comes with Ubuntu, if you can and are not already, and see if that helps at all.

First, what does executing this on the terminal (Applications > Accessories > Terminal) print?
```
$ locale
```

Second, try doing either of these (depending on which you've installed) on the terminal:
```
$ LANG=en_US.UTF-8 mc
$ LANG=en_GB.UTF-8 mc
```

Third, try to change the font your terminal is using.
I cannot help much with this step, though.

---

### Post by rensu on 2006-01-08
Tried both of the lines but nothing changes.
$ locale
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

That's what it reports when i write locale.

---

