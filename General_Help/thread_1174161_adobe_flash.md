---
title: "adobe flash"
date: 2009-05-30
forum: General Help
---

### Post by Dave Otter on 2009-05-30
Whenever I try to watch any program that uses Adobe Flash Player I get an error that says the latest version is required to view this  site.
  I go to download to be told a later version is already installed.
  I have tried uninstalling and then reloading but to no avail.
   What am I missing?

Help!

---

### Post by philinux on 2009-05-30
Sounds like you may have more than one flash installed. 

In a terminal use this first

```
sudo updatedb
```

Then post back the output of this

```
locate libflashplayer.so
```


Also check in firefox Tools>addons>plugins to see which flash player version firefox has.

---

### Post by hyperdude111 on 2009-05-30
sudo apt-get install ubuntu-restricted-extras

---

### Post by Dave Otter on 2009-06-01
Output of 'locate libflashplayer.so 

                /usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/opera/plugins/libflashplayer.so

---

