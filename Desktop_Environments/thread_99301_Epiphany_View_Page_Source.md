---
title: "Epiphany View Page Source"
date: 2005-12-05
forum: Desktop Environments
---

### Post by psychicdragon on 2005-12-05
Anyone know how to configure what application Epiphany uses to view the page source? If you have Gedit installed it uses that by default, but if not it tries to use Abiword (wtf!?)

There's no gconf key that I could find, and it doesn't follow the file-association from Nautilus. Does it use dark magic to determine what application to use if Gedit's not present, or am I missing something?

---

### Post by webograph on 2007-07-28
it does follow the nautilus settings, at least in the current svn version; more precisely, it uses whichever editor is set up for the "text/plain" mime type in the gnome-vfs settings (which are accessed through nautilus).

---

