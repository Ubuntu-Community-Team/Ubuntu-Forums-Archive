---
title: "Console coloured display"
date: 2009-11-19
forum: Desktop Environments
---

### Post by mudcow007 on 2009-11-19
hello all we currently have a Feisty Fawn machine with a gui, when you use the cli some text comes up as a different colour. this is really useful for noticing faults etc

gnome terminal 2.18.0

i have just installed Jaunty Jackalope and the terminal is mono coloured, making it a nightmare to spot errors!

gnome terminal 2.26.0

i have tried installing Konsole but thats the same (one colour)

any ideas?

---

### Post by Giblet5 on 2009-11-19
Both terminals (Gnome or Konsole) are color capable.

Run this command: ```
ls /etc
```

Colorful, no?

These terminal programs are not The Console though. To see the console, hit Ctrl+Alt+F1. THAT is the console and it is color-enabled as well. To get back, hit Ctrl+Alt+F7.

Gnome terminal, and konsole, understand escape sequences that provide up to 16 colors. The escape sequences for color are defined by the [ANSI code sequences]("http://en.wikipedia.org/wiki/ANSI_escape_code").

You can turn colors off in both terminals. For example on Gnome terminal, click Edit -> Profile Preferences -> Colors tab...

---

### Post by mudcow007 on 2009-12-14
hi Giblet sorry only just seen your reply!

thanks for the info :)

---

### Post by mudcow007 on 2009-12-15
hello all

i have followed "Giblet's" advice but im still not seeing colour on my console.

im using GNOME terminal 2.26.0

when i use the command ```
ls /etc
``` i see different colours but when i run Asterisk all i see is black and white.

in "colors" within the terminal its currently set to "Use colors from system theme"

i have also just tried the "Konsole" that also doesnt show colours when running Asterisk :(

---

