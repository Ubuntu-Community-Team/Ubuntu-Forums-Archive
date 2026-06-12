---
title: "Removed /.config/autostart entry -- but it's still starting!!"
date: 2007-01-05
forum: Desktop Environments
---

### Post by wilberfan on 2007-01-05
I had an entry in /home/me/.config/autostart to fire up gdesklets until recently.   I decided I liked gkrellm better, so I removed the .desktop entry in autostart -- but gdesklets STILL STARTS AT BOOT.

WTF?   

I checked System/Preferences/Session but there's nothing there...    What could be starting that program --and how do I get it to stop?!

---

### Post by teaker1s on 2007-01-05
/etc/rc.local  look for it in there

---

### Post by wilberfan on 2007-01-05
> **teaker1s said:**
> /etc/rc.local  look for it in there

Hmmm...  I don't have a rc.local folder...   I have rc0.d, rc1.d, rc2.d, etc...but I don't see anything about gdesklets in there...  :-k

[edit] Correction.   I DO have an rc.local *file* -- but this is the contents:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
```

---

### Post by wilberfan on 2007-01-07
Just for the record, I ended up uninstalling gDesklets (!) to see if THAT would make it stop loading--but then I discovered that there were some OTHER gdesklets.desktop files.   Two more to be exact...   One was in /var/lib/gnome/Debian/Apps/Tools/gdesklets.desktop and the other...oh, crap...i've forgotten....   (I found them by doing a search.)

Anyway, NOW the little buggers don't show up at startup anymore!  ;)

---

