---
title: "Conky"
date: 2006-11-16
forum: Desktop Environments
---

### Post by dmsn on 2006-11-16
Hey 
I wonder if i can get conky to run many .conkyrc files
i want them not on same place on my desktop.

---

### Post by mark_g on 2006-11-16
No, but you can start multiple instances of Conky, each with a different configuration file.
So if you copy the configfile and change the positioning, you'll see two conky's on your desktop.

conky
 to start with the default config file

conky -c /path/to/other/edited/configfile
 to start the second instance with your other configfile

---

