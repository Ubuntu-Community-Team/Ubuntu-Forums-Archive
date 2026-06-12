---
title: "Crontab starts deluge without my settings or torrents"
date: 2009-12-06
forum: Desktop Environments
---

### Post by Garrek42 on 2009-12-06
Here's the line from my crontab:

15 9 * * *    root export DISPLAY=:0 && /usr/bin/deluge

Deluge starts up, but with out the settings or torrent files I get if I either click the task bar option, or run the command from the command line. I've uninstalled and reinstalled, but with no improvement. Any suggestions would be helpful. I'm using Karmic Koala, and it's up to date.

---

### Post by akashiraffee on 2009-12-06
> **Garrek42 said:**
> 
15 9 * * *    [COLOR=Red]root [/COLOR]export DISPLAY=:0 && /usr/bin/deluge


Why do you have "root" there?  Did crontab put that there?

Did you run crontab sudo?  If so, "your" crontab is really the root one.  If you have to use sudo, use -u yourusername.

---

### Post by Garrek42 on 2009-12-07
Yeah, my friend said that to me when I asked him... I changed it to the correct user name, works like a charm... My bad...  Thanks

---

