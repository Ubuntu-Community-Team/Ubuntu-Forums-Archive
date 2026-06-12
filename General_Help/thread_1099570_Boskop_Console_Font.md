---
title: "Boskop Console Font"
date: 2009-03-18
forum: General Help
---

### Post by snowsmash on 2009-03-18
I used to like the Boskop console font (see link at the bottom), and I used to use it in Ubuntu pre-8.10, loading it using consolechars with no problems. With 8.10, when I attempt to set the font using setfont, all characters on the console turn into question marks. (Doing a force-reload on console-setup resets the screen afterwards.) I do not run into this problem with other fonts in /usr/share/consolefonts. Any suggestions on how to investigate this further are appreciated.

[http://www.scribusstuff.org/content/show.php/Boskop+Console+Font?content=19621&PHPSESSID=6a36ac527830ac70bd39cb4b4e13fed2](http://www.scribusstuff.org/content/show.php/Boskop+Console+Font?content=19621&PHPSESSID=6a36ac527830ac70bd39cb4b4e13fed2)

Youssef Eldakar
Bibliotheca Alexandrina

---

### Post by snowsmash on 2009-04-01
I figured it out. The console was set to UTF-8, and the font in question is apparently not compatible with UTF-8. To set the console to the default character set, echo -n -e '\033%@' into the cosnole device (e.g. /dev/tty1) or, for a persistent setting, set CHARMAP="ISO-8859-1" in /etc/default/console-setup.

Youssef Eldakar
Bibliotheca Alexandrina

---

