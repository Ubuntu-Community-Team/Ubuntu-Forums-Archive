---
title: "Opening on another desktop?"
date: 2005-07-24
forum: Desktop Environments
---

### Post by ubuntp on 2005-07-24
How can i make an application, lets say xxms, always open on desktop 2? Or make the download window in Epiphany/Firefox always appear on desktop 4?

---

### Post by charlieg on 2005-07-24
I'm not sure you can!?  I've never heard of that before.  I think it's down to the user to switch to the desired desktop before loading up the app.

---

### Post by marguz on 2005-07-25
It has to do with youre windows manager. FVWM is one that (if I remember corectly) can do it.

---

### Post by Majlo on 2005-07-26
[QUOTE=ubuntp]How can i make an application, lets say xxms, always open on desktop 2? Or make the download window in Epiphany/Firefox always appear on desktop 4?[/QUOTE]

Hi
Yes you can..Just install program devilspie

sudo apt-get install devilspie

Then :

cp /usr/share/doc/devilspie/examples/sample-config.xml ~/.devilspie.xml

And look to ~/.devilspie.xml and write you configuration.Its simply

And at the end open System --> Preferences --> Sessions --> Startup Program and add devilspie .

PS: Info how edit ~/.devilspie.xml is in /usr/share/doc/devilspie/README.gz

---

### Post by ubuntp on 2005-07-26
thanks.

---

